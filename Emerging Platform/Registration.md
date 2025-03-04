---
stoplight-id: 8fmelqkzamfsk
---

# Registration

## Overview
The registration process is fundamental to adding entities as digital twins in the Spatial Web. Domains are identified using self-sovereign digital identifiers (DIDs), following the Interchain Identifier DID Methodology. The `Entity` Module generates deterministic identifiers that can be cryptographically authenticated and each domain is established as a digital twin entity

The Interchain Identifier (`IID`) Module of the blockchain manages a registry for these identifiers, with their relevant metadata and domain documents. [Learn about the types of Entities](Registry.md) in this registry. 

Each Entity Domain is encoded as an NFT, making the domain ownable and transferrable.

## Metadata Associated with Entities
- **Relayer Node**: Identifies the domain through which the entity was created. This is significant for jurisdictional compliance and the distribution of platform fees generated when the entity uses network services like Oracles.
- **Validity Period**: Optional dates that define when the entity is valid.
- **Status**: The state set by the entity controller (e.g., "Deactivated").
- **Verified**: Indicates whether the entity is verified within the domain, set by the Market Relayer through an on-chain governance process.
- **Credentials**: An array of credential identifiers that can provide public proofs of credentials, managed by the entity controller in a privacy-preserving manner.

## Domain Types for Modern Energy Cooking
The domain ontology outlines the structure of interconnected entities within the Modern Energy Cooking system. These include:
- **Organizations**: Instantiated as DAOs
- **Projects**
- **Devices**: Managed in Asset Collections or as individual assets
- **Protocols**
- **Oracles**: Provide services like claim processing using dMRV protocols
- **Deeds**: Represent proposals, claim collections, and manage offers

## Creating an Entity
To instantiate a new entity, the first step is to create or reference an existing Protocol. A Protocol defines the `class` and common `properties` that all entities of this class inherit. Each entity document specifies its class under the `@context` field, with a key "class" and value like `did:ixo:entity:abc123`.

To create a new entity, follow the [Creating an Entity implementation guide](../../Implementation-Guides/Create-Query-Entity.md).

## Protocol Templates
The Emerging Platform includes a number of Protocol Templates that are specific to the use-case. These define schemas for claims, credentials, data models, documentation templates, and entity class properties. To view available protocols, query the Blocksync chain index database for the Emerging Market Relayer identifier and filter for entities of type `Protocol`.

```graphql
query EntitiesByRelayerNodeAndType {
  entities(
    filter: {relayerNode: {equalTo: "did:ixo:entity:a1fcead81eab2f1158a726597d872413"}, type: {equalTo: "protocol"}}
  ) {
    totalCount
  }
}
```

## Governance
The Market Relayer operator is responsible for setting the **Verified** status of entities. Any member of the Emerging DAO Compliance Group can submit a proposal to update an entity's Verified status to `true` or `false`. Compliance Group members vote on these proposals using an on-chain governance mechanism. Upon passing the proposal with the quorum and consensus settings, the chain automatically executes `msgVerifyEntity`.

A standardized Deed Protocol is available for carrying out this governance procedure.
