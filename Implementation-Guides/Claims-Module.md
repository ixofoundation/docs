---
stoplight-id: 0zq7g0lz3gh5b
---

# Create Claims and Collections

## Step-by-Step Guide

This guide will walk you through the process of creating a new claim collection using the **IXO Spatial Web Multiclient SDK** and then submitting a claim to the collection. We will leverage the `CreateCollection` and `MsgExecAgentSubmit` functions to illustrate how to create claims and collections on the IXO blockchain.

### Step 1: Create a Collection

To create a new collection, use the `CreateCollection` function provided by the IXO Spatial Web Multiclient SDK. Below is an example that demonstrates how to create a collection in TypeScript:

```typescript
const response = await CreateCollection(
  "entityDid1234",      // The DID of the entity creating the collection
  "protocolDid1234",    // The DID of the associated protocol
  "paymentsAccount1234" // Account to handle payments
);
```

In this example, the `CreateCollection` function is invoked to create a new collection. The parameters include:

- **entityDid**: The DID of the entity creating the collection.
- **protocolDid**: The DID of the protocol under which the collection falls.
- **paymentsAccount**: Account to handle collection-related payments.

This function sets up a collection where claims can be submitted, evaluated, and finalized. It also defines various parameters like start and end dates, quotas, and payment details.

### Step 2: Retrieve Collection Data Using GraphQL

After creating a collection and submitting a claim, you can retrieve the data related to the collection and claims using the IXO Blocksync GraphQL API.

Here is an example GraphQL query to retrieve details about a specific collection:

```graphql
query MyQuery {
  claimCollection(id: "99") {
    id
    startDate
    endDate
    entity
    protocol
    admin
    count
    evaluated
    approved
    rejected
    disputed
    claimSchemaTypesLoaded
    invalidated
    payments
    quota
    state
  }
}
```

### Step 3: Submit a Claim to the Collection

Once the collection is created, you can proceed to submit a claim to this collection. This can be done using the `MsgExecAgentSubmit` function, which is designed to help agents submit claims for evaluation.

Here is an example:

```typescript
const response = await MsgExecAgentSubmit(
  "claimId1234",        // Unique identifier for the claim
  "collectionId1234",   // Identifier of the collection
  "adminAddress1234"    // Admin address authorizing the claim submission
);
```

In this example, the `MsgExecAgentSubmit` function is invoked to submit a claim. The parameters include:

- **claimId**: A unique identifier for the claim being submitted.
- **collectionId**: The collection to which the claim belongs.
- **adminAddress**: The admin address authorizing the submission.

Replace the `id` field with the **collection ID** you obtained during collection creation to get specific details.

This query will provide you with comprehensive information about the collection, including its state, start and end dates, payment details, and more. It is useful for verifying the collection's configuration and understanding its status.

Here is an example:

```typescript
const response = await MsgExecAgentSubmit(
  "claimId1234",        // Unique identifier for the claim
  "collectionId1234",   // Identifier of the collection
  "adminAddress1234"    // Admin address authorizing the claim submission
);
```

In this example, the `MsgExecAgentSubmit` function is invoked to submit a claim. The parameters include:

- **claimId**: A unique identifier for the claim being submitted.
- **collectionId**: The collection to which the claim belongs.
- **adminAddress**: The admin address authorizing the submission.

### Step 4: Retrieve Claim Data Using GraphQL

```graphql
query MyQuery {
  claim(claimId: "bafkreihzugslzexyu2c6o6nmtm7vxbsyelo7pzmcppsmqawj2s6blmgojy") {
    schemaType
    claimId
    agentAddress
    agentDid
    collectionId
    paymentsStatus
    submissionDate
  }
}
```

## Step 5: Evaluate a Claim

Once a claim has been submitted, it can be evaluated using the `MsgExecAgentEvaluate` function. This function allows an agent to assess the claim and determine its status.

Here is an example of how to use the `MsgExecAgentEvaluate` function:

```typescript
const response = await MsgExecAgentEvaluate(
  "claimId1234",        // Unique identifier for the claim
  "collectionId1234",   // Identifier of the collection
  "adminAddress1234"    // Admin address authorizing the claim evaluation
);
```

In this example, the `MsgExecAgentEvaluate` function is invoked to evaluate a claim. The parameters include:

- **claimId**: A unique identifier for the claim being evaluated.
- **collectionId**: The collection to which the claim belongs.
- **adminAddress**: The admin address authorizing the evaluation.

### Step 6: View the Claim Using GraphQL

After a claim has been evaluated, you can use the IXO Blocksync GraphQL API to view the details of the claim, including its evaluation status.

Here is an example GraphQL query to retrieve the details of a specific claim:

```graphql
query MyQuery {
  claim(claimId: "bafkreihzugslzexyu2c6o6nmtm7vxbsyelo7pzmcppsmqawj2s6blmgojy") {
    schemaType
    claimId
    agentAddress
    agentDid
    collectionId
    paymentsStatus
    submissionDate
    evaluationByClaimId {
      status
      verificationProof
      amount
      evaluationDate
      oracle
      reason
    }
  }
}
```

Replace the `claimId` field with the **claim ID** you obtained during claim submission to get specific details.

This query will provide detailed information about the claim, including its status, submission date, evaluation details, and related metadata. It is useful for verifying the claim's status and understanding the outcome of the evaluation.

## Claims Module

### Functions:
- **CreateCollection**: Creates a new collection on the IXO blockchain.
- **UpdateCollectionState**: Updates the state of a collection, such as opening or closing it.
- **UpdateCollectionIntents**: Updates the intent settings for a collection.
- **UpdateCollectionDates**: Modifies the start and end dates for a collection.
- **UpdateCollectionPayments**: Updates the payment information associated with a collection.
- **DisputeClaim**: Initiates a dispute for a specific claim.
- **GrantEntityAccountClaimsSubmitAuthz**: Grants authorization for claim submission to an entity account.
- **MsgClaimIntent**: Submits an intent for a claim against a collection.
- **MsgExecAgentSubmit**: Executes the submission of a claim by an agent using authorization.
- **GrantEntityAccountClaimsEvaluateAuthz**: Grants claim evaluation authorization to an entity account.
- **GrantEntityAccountClaimsEvaluateAuthzThroughAuthz**: Grants claim evaluation authorization through existing authorizations.
- **MsgExecAgentEvaluate**: Executes an evaluation of a claim, determining its approval status.
- **MsgExecWithdrawal**: Executes a withdrawal of a payment related to a claim.
- **CreateCollectionSupamotoGenesis**: Creates a special Genesis Collection for Supamoto.
- **GrantEntityAccountClaimsEvaluateAuthzSupamoto**: Grants claim evaluation authorization specifically for the Supamoto Genesis collection.

