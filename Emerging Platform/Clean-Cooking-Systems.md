---
stoplight-id: e5aip4bsyi1ki
---

# Mitigation Activity Systems

### Cognitive Digital Twins

The IXO Spatial Web implements a systems-thinking approach to capture relationships, feedback loops, and interdependencies in the real-world systems through which mitigation activities are coordinated, financed, verified, governed, and intelligently optimised. 

Each physical or conceptual element is represented digitally as a _Digital Entity_ with a digital **Domain**.

#### What is a Digital Entity?
A Digital Entity is the online “twin” of a real-world object or concept. Examples include:  
- Physical entities (e.g., modern energy cooking devices)  
- Cognitive entities (such as organizations, projects, investment vehicles, and assets)

#### What is a Digital Domain?
A Domain in the IXO Spatial Web is a unique, verifiably owned digital entity that represents a real-world entity, identified by a DID and controlled by the holders of specified public keys or blockchain accounts. It integrates various internet-based services for functionality, manages resources such as documents or media through URI references (often backed by cryptographic proofs), and defines explicit rights for who can perform particular actions via object capabilities and other secure authentication mechanisms. Domains can record verified data (“linked claims”) that update their state, and they connect to other entities (like oracles and projects) to form interoperable virtual networks. Serving as economic actors, they hold blockchain accounts for digital financing activities and are represented as NFTs, allowing for seamless transfer of ownership and interaction across decentralized ecosystems.

#### Identifying Entities and their Domains  
Decentralized Identifiers (DIDs) provide a unique identity for each Entity and its Domain. A DID is cryptographically verifiable and self-sovereign, guaranteeing that data ownership and control of the Ebtity Domain belongs to its Creator or Controller. This approach upholds:  
- Uniqueness: Each entity has its own traceable ID.  
- Trust: Verifiable cryptographic proofs ensure authenticity.  
- Self-Sovereignty: Full ownership by the entity creator/controller.

#### Relationships Between Entities

Entities are nodes within a rich data graph in which entities are connected by relationships that represent how they interact, influence, and impact on each other.

Relationship Examples:  
- A Mitigation Activity proponent **organization** `implements` a **project**  
- An investor **organisation** `funds` a **project** 
- Funding to the  **project** is from an `allocation` of capital through an **investment** instrument   
- **Assets** are `generated` through a **project**  
- Claims from **project** activities are `verified` by an **Oracle** Service  

#### The Impact Graph   
1. Captures Immutable Data Streams: Post-hoc data manipulation is impractical due to blockchain integrity.  
2. Enables Systems-Level Analysis: Offers a big-picture view, suitable for holistic monitoring and optimization.  
3. Strengthens Trust: Transparent accountability fosters higher confidence among stakeholders and auditors.

#### Data Integrity
Ensuring data integrity is vital to preventing fraudulent mitigation outcome claims and thwarting attacks aimed at compromising trust in climate impact records. The Platform design and how it is operated [assures data integrity](Emerging Platform/Data-Integrity.md).

#### Data Fusion
Data from real-world systems is fused into the digital twin system through Verifiable Claims. These Claims are processed through verification processes that results in Verifiable Credentials (digital certificates) being issued. This enables tokenized outcomes (Impact Credits) to be minted, representing the verifiable units of measured, reported and verified outcomes that are generated through the digital twin system, which mirrors the claimed and verified changes that have ocurred over time in the real-world system.

### Digital Domain Setup

Entities and their relationships are [registered](Emerging Platform/Registration.md) in the platform as _domains_ and each domain is configured with its Domain Properties:  
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
