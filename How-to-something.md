---
stoplight-id: jltzpgiodtir6
---

# How to something

## Prerequisites

- Make sure the required SDKs have been installed for your application.
  - If you are using the [Multiclient SDK](IXO-Spatial-Web-Multiclient-SDK.md), make sure that you understand how to use the [Signing Client](https://www.npmjs.com/package/@ixo/impactxclient-sdk#signing-client).
- Make sure that you understand how to use the [IXO Blocksync GraphQL](Blocksync-GraphQL-API-Overview.md) queries.

## Steps

In order to create a new entity, use the SDK in a similar way to this Typescript test:
```typescript
    let entityDid;
    testMsg("/ixo.entity.v1beta1.MsgCreateEntity asset", async () => {
      const res = await Entity.CreateEntity();
      entityDid = utils.common.getValueFromEvents(res, "wasm", "token_id");
      console.log({ entityDid });
      return res;
    });
```

The test invokes the `CreateEntity` function in the module named Entity.ts:
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
Test is [here](https://vscode.dev/github/ixofoundation/ixo-multiclient-sdk/blob/main/__tests__/flows/entities.ts#L17)

Entity.js class is [here](https://vscode.dev/github/ixofoundation/ixo-multiclient-sdk/blob/main/__tests__/modules/Entity.ts)

Once you have created the entity and you have logged the entity's DID, then you can query the GraphQL endpoint directly to retrieve details for the entity.
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
In a similar manner, you can update the entity and perform the other functions available in the Entity.js module.