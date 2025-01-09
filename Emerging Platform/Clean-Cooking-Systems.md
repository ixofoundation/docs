---
stoplight-id: e5aip4bsyi1ki
---

# Clean-Cooking-Systems

### Cognitive Digital Twin Systems

The IXO Spatial Web implements a systems-thinking approach to capture relationships, feedback loops, and interdependencies in real-world environments. Each physical or conceptual element is represented digitally as a _Digital Entity_ that has its own Domain.

#### What is a Digital Entity?
A Digital Entity is the online “twin” of a real-world object or concept. Examples include:  
- Physical entities (clean cooking stoves, modern energy devices)  
- Cognitive entities (organizations, projects, and assets)

#### Identifying Entities  
DIDs, based on the W3C DID specification, provide unique identities. Each DID is cryptographically verifiable and self-sovereign, guaranteeing that data ownership and control remain with its originator. This approach upholds:  
- Uniqueness: Each entity has its own traceable ID.  
- Trust: Verifiable cryptographic proofs ensure authenticity.  
- Self-Sovereignty: Full ownership by the entity creator.

#### Relationships Between Entities

Entities form nodes within a rich data graph, connected by relationships representing how these nodes interact or impact each other.

Relationship Examples:  
- An organization implements a project.  
- A project is funded by an investor.  
- Assets are generated through a project.  
- Claims from project activities are verified by Oracles (AI-enabled probabilistic evaluators).  
- The verification process results in verifiable credentials (digital certificates).  
- Verifiable credentials enable tokenized outcomes (impact credits).

#### Graph Representation  
Each entity—along with its claims and connections—builds a time-sequenced, tamper-evident digital graph that:  
1. Captures Immutable Data Streams: Post-hoc data manipulation is impractical due to blockchain integrity.  
2. Enables Systems-Level Analysis: Offers a big-picture view, suitable for holistic monitoring and optimization.  
3. Strengthens Trust: Transparent accountability fosters higher confidence among stakeholders and auditors.

### Registration and Digital Domain Setup

Entities and their relationships are registered on the blockchain as _domains_. Each domain (e.g., organization, project, asset, protocol) reflects a unique context within the network.

Domain Properties:  
1. Digital Identifier  
   Created as a DID for verifiable ownership and uniqueness; can be enhanced with verifiable credentials.  
2. Domain Controllers  
   Defined by public keys or blockchain accounts. Only those with permission can update a domain’s data.  
3. Services  
   Internet-based services tied to the domain, providing necessary functionalities (e.g., data ingestion endpoints).  
4. Linked Resources  
   Digital materials (documents, media) referenced via URIs, often with cryptographic proofs for authenticity.  
5. Accorded Rights  
   Object capabilities (zCAPs, Cacao) specify who can perform specific actions, preserving privacy and security.  
6. Linked Claims  
   Verified data items that update the domain’s state (e.g., device usage records, fuel delivery confirmations).  
7. Linked Entities  
   Builds a network of related domains—such as funders, projects, or oracles—and formalizes their interconnections.  
8. Economic Accounts  
   Domains function as economic actors with blockchain accounts, enabling DeFi-related actions (e.g., staking, payments).  
9. Non-Fungible Tokens (NFTs)  
   Each domain is represented as an NFT, facilitating ownership transfers and interactions with other decentralized ecosystems.

## Using Protocols

Manually configuring domains can be intricate, so the IXO platform offers _Protocols_ to streamline the process. A protocol is a predefined template of properties, relationships, and data models for a specific type of domain.

### Instantiating Protocols  
When developers create an entity from a protocol “class,” it inherits the protocol’s default configurations. These inherited settings can be forked and updated to fit the specific use case, promoting:  
- Rapid deployment of standard domain types.  
- Consistent data structures across projects.  
- Hierarchical organization, allowing child entities to trace back to a parent protocol.

Example: Climate Mitigation Project Protocol  
A protocol designed for clean cooking initiatives can include:  
- Default data fields (fuel types, reporting standards, usage metrics).  
- Relationships (verification oracles, project developers, funders).  
- Services (data analytics, payment frameworks, governance tools).
