# Fees Module

## Fees

The Entity Document `fees` property has the struct:

```go
type ProjectFeesMap struct {
Context string `json:"@context" yaml:"@context"`
Items   []struct {
Type              FeeType `json:"@type" yaml:"@type"`
PaymentTemplateId string  `json:"id" yaml:"id"`
}
}
```

Here is an example of how `fees` are specified in a project's `data`:

```json
"data": {
    ...
    "fees": {
        "@context": "https://w3id.org/ixo/ns",
        "items": [
            {
                "@type": "OracleFee",
                "id":"payment:template:oracle-fee-template-1"
            },
            {
                "@type": "FeeForService", 
                "id":"payment:template:fee-for-service-template-1"
            }
        ]
    }
    ...
}
```

The project-related fees currently supported are:

* Oracle Fee (`OracleFee`)
* Fee for Service (`FeeForService`)

### General Approach

The Entity Document `fees` property specifies one or more **payment template** IDs for pre-created payment templates. Each Payment Template specifies details such as the payment amounts, minimums, maximums, etc (see the payments module spec).

For payments to be made requires the creation of a **payment contract**. Payment contracts effect `msgSend` transactions, when specific conditions are satisfied.

The `processPay` function is used to create a contract and effect payments. A simplified version of this function is presented below:

```go
func processPay(keepers, projectDid, senderAddr, recipients, feeType, paymentTemplateId) {

// Validate recipients
recipients.Validate()

// Get project address
projectAddr := getProjectAccountAddress()

// Get payment template
template := paymentsKeeper.GetPaymentTemplate(paymentTemplateId)

// Contruct payment contract ID
contractId := "payment:contract:<moduleName>:<projectDid>:<senderAddr>:<feeType>"

// Get an existing payment contract, or create a new contract
if paymentsKeeper.ContractExists(contractId) {
contract = paymentsKeeper.GetPaymentContract(contractId)
} else {
// Create a new contract with the constructed contractId. This points to a
// specified payment template, with the project as the creator and payer in this example,
// with the specified recipients. The contract cannot be deauthorised and is
// by default authorised (i.e. can be effected by the contract creator).
contract = payments.NewPaymentContract(contractId, paymentTemplateId,
projectAddr, projectAddr, recipients, false, true)
paymentsKeeper.SavePaymentContract(contract)
}

// Effect payment if conditons are met
if contract.CanEffectPayment {
// Check that project account has sufficient tokens to effect the payment contract
if !bankKeeper.HasCoins(projectAddr, template.PaymentAmount) {
return error("project has insufficient funds")
}

// Effect payment
paymentsKeeper.EffectPayment(contractId)
} else {
return error("cannot effect contract payment (max reached?)")
}
}
```

The payment contract ID is automatically created using the following syntax:

* Syntax: `payment:contract:<moduleName>:<projectDid>:<senderAddr>:<feeType>`
* Example: `payment:contract:project:did:ixo:U7G...J8c:ixo107...0vx:OracleFee` Each payment contract is a unique instance for a module, project, sender address and fee type.

Thus, if a new and unique set of the above 4 values is encountered, a new payment contract is created. Otherwise, the existing payment contract is fetched. This means that the project contract can (and is) used to persist information between two or more payments of the same type.

An example use case is when we want to specify a maximum payment. Consider a contract created based on a payment template that specifies a pay amount of 100IXO and a maximum of 300IXO.

1. In the first `processPay()` call, a new payment contract is created and immediately effected (cumulative pay: `100IXO`)
2. In the second `processPay()` call, the payment contract already exists and is fetched and the payment is effected (cumulative pay: `200IXO`).
3. In the third `processPay()` call, the cumulative pay will have reached the maximum `300IXO`.
4. If a fourth `processPay()` call comes through, no further payment is effected, given that the contract cannot be effected due to the maximum being reached.

If the project does not have enough funds to effect the payment contract, an error is returned by the function. An error is also returned if the payment contract payment cannot be effected.

### Types of Fees

#### Oracle Fee

If an `oracle fee` payment template ID is specified when an entity is created, the oracle fee payment is made whenever an oracle processes a claim using the function `MsgCreateEvaluation`. Fees are automatically sent from the entity's project account to the oracle service-provider and any other fee recipient addresses specified in the payment contract.

#### Fee for Service

If a `fee-for-service` payment template ID is specified when an entity is created, the contract fee amount is automatically sent from the entity's project account to the service agent's account. The transaction is automatically processed when the service agent submits a claim, or when the claim status changes, depending on the condition for payment. For instance, the agent is paid when a claim is approved (the claim status updates to `1`) during `MsgCreateEvaluation` message flow.
