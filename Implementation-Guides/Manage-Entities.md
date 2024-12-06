---
stoplight-id: n44c05pypw2gu
---

# Creating an Entity

## Step-by-Step Guide

This guide will walk you through the process of creating a new entity using the **IXO Spatial Web Multiclient SDK** and then viewing the entity using a **GraphQL query** to the IXO Blocksync API.

### Step 1: Create an Entity

To create a new entity, use the `CreateEntity` function provided by the IXO Spatial Web Multiclient SDK. Below is an example that demonstrates how to create an entity in TypeScript:

```typescript
let entityDid;
testMsg("/ixo.entity.v1beta1.MsgCreateEntity asset", async () => {
  const res = await Entity.CreateEntity();
  entityDid = utils.common.getValueFromEvents(res, "wasm", "token_id");
  console.log({ entityDid });
  return res;
});
```

<!-- theme: info -->

> #### Protocols as canonical classes 
>
> To instantiate a new entity, the first step is to create or reference an existing Protocol. This Protocol defines the class and common properties that all entities of this class inherit. Each entity document specifies its class under the `@context` field, with a key `class` and value like `did:ixo:entity:abc123`.

In this example, the `CreateEntity` function is invoked to create a new entity, and the returned **entity DID** is logged to the console. The `entityDid` value will be required in the next step to query the entity details.

The `CreateEntity` function is defined in the `Entity.ts` module and has the following structure:

```typescript
export const CreateEntity = async (
  entityType: string = "asset",
  context?: [{ key: string; val: string }],
  relayerNodeDid = "",
  relayerNode: WalletUsers = WalletUsers.tester,
  signer: WalletUsers = WalletUsers.tester
) => {
  const client = await createClient(getUser(signer));

  const tester = getUser(signer);
  const account = (await tester.getAccounts())[0];
  const myAddress = account.address;
  const myPubKey = account.pubkey;
  const did = tester.did;

  const relayerNodeDidLocal = relayerNodeDid || getUser(relayerNode).did;

  const message = {
    typeUrl: "/ixo.entity.v1beta1.MsgCreateEntity",
    value: ixo.entity.v1beta1.MsgCreateEntity.fromPartial({
      entityType: entityType,
      context: createAgentIidContext(context),
      verification: createIidVerificationMethods({
        did,
        pubkey: myPubKey,
        address: myAddress,
        controller: did,
        type: keyType,
      }),
      controller: [did],
      ownerDid: did,
      ownerAddress: myAddress,
      relayerNode: relayerNodeDidLocal,
    }),
  };

  const response = await client.signAndBroadcast(
    myAddress,
    [message],
    getFee(1, await client.simulate(myAddress, [message], undefined))
  );
  return response;
};
```

In this function:

- **client** is used to sign and broadcast the transaction.
- **entityType** defines the type of entity to be created (e.g., "asset").
- **context** provides additional metadata, while **verification** and **controller** secure and validate the entity.

You can find more details about the `CreateEntity` function in the SDK [Entity module](https://github.com/ixofoundation/ixo-multiclient-sdk/blob/main/__tests__/modules/Entity.ts).

### Step 2: Retrieve the Entity Using GraphQL

Once the entity is created and you have logged the **entity DID**, you can query the IXO Blocksync GraphQL endpoint to retrieve the details of the entity. Use the following GraphQL query to fetch the entity's data:

```graphql
query MyQuery {
  entity(id: "did:ixo:entity:eaff254f2fc62aefca0d831bc7361c14") {
    id
    type
    owner
    relayerNode
    startDate
    endDate
    metadata
    entityVerified
    controller
    verificationMethod
    service
    status
    settings
    accordedRight
    accounts
    alsoKnownAs
    assertionMethod
    authentication
    capabilityDelegation
    capabilityInvocation
    context
    credentials
    externalId
    linkedResource
    linkedEntity
    keyAgreement
    linkedClaim
  }
}
```

Replace the `id` field with the **entity DID** obtained from the previous step to get the specific details of your entity.

This query will provide you with comprehensive information about the entity, including its type, owner, relayer node, status, linked claims, and other metadata. It is useful for verifying that the entity has been successfully registered on the blockchain and understanding its state and relationships.

### Step 3: Update the Entity (Optional)

You can also use the **Entity** module to update the entity after it has been created. The SDK provides several methods for performing operations on existing entities, such as updating their context, ownership, or linked resources.

Refer to the Entity module for more information on available functions for managing entities.

## Entity Module

### Functions:
- **CreateEntity**: Creates a new entity on the IXO blockchain.
- **TransferEntity**: Transfers ownership of an entity to another party.
- **UpdateEntity**: Updates details of an existing entity, such as status, dates, or credentials.
- **UpdateEntityVerified**: Updates the verification status of an entity.
- **CreateEntityAccount**: Creates a new account for the specified entity.
- **GrantEntityAccountAuthz**: Grants authorization to another account to manage or perform actions related to the entity account.
- **MsgRevokeEntityAccountAuthz**: Revokes a previously granted authorization for an entity account.

