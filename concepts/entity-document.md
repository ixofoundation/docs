---
description: The digital building-block of ixo Protocol Networks.
---

# ixo Documents

A special type of **digital document** is the digital building-block of ixo Protocol Networks. An ixo document, together with its associated Decentralised Identifier \(DID\), identifies and describes each entity in an ixo protocol network. This should become interoperable with all other networks that implement the new W3C Internet standards for decentralised internets. 

The ixo Document also associates cryptographic objects with an entity. This gives the entity remarkable capabilities, such as sovereign control over its own identifier and the ability to authenticate with services, using keys that are referenced in the network's decentralised public key infrastructure.

## What is an ixo Entity?

The Internet of Impact is formed by inter-connected decentralised networks of both physical infrastructure and virtual data nodes. Every node which  implements the ixo protocol standards can be described as an **ixo Entity.** \(The ixo protocol implements core new web standards from W3C\). 

An ixo Entity has an identity and an associated store of information. The ixo Document provides the genesis record for this information and can maintain a core record of the entity's information and connections. This includes specifying end-points for locating other information and services that are associated with the entity.  

Entities connect to other entities, using cryptographic proofs. These authenticated connections form [Webs of Trust](https://en.wikipedia.org/wiki/Web_of_trust), through which information and value can securely flow. 

By subscribing to standard data models and open schemas, entity nodes and the connections \(edges\) beween these nodes form an ontologically rich and precise knowledge-graph. These graphs can be searched and navigated through the Internet of Impact and hyperlinked into Web 2.0 networks.  

#### Entities in the context of ixo protocol networks

An entity in the context of ixo can be a:

* Cell
* Project
* Oracle
* Fund \("smart contract"\)
* Data Asset
* Relayer
* Agent \(person, organisation or machine\)

Each Entity has an identity, which is defined by a [Decentralised Identifier](https://www.w3.org/TR/did-core/) \(DID\). 

## What is an ixo document?

An entity is described by information contained in a standard Document format - the [DID Document \(DDO\)](https://www.w3.org/TR/did-core/#core-properties).

{% hint style="info" %}
**A DID Document** is a set of data describing an Entity Node \(the [DID subject](https://www.w3.org/TR/did-core/#dfn-did-subjects)\) in ixo protocol networks. The DDO includes mechanisms, such as cryptographic public keys, that the [DID subject](https://www.w3.org/TR/did-core/#dfn-did-subjects) can use to authenticate itself, to prove their association with the [DID](https://www.w3.org/TR/did-core/#dfn-decentralized-identifiers) and to be given electronic rights \(capabilities\). A DID document might also contain other [attributes](https://en.wikipedia.org/wiki/Attribute_%28computing%29) or [claims](https://en.wikipedia.org/wiki/Claims-based_identity) that describe the subject. These documents are graph-based data structures which the ixo protocol expresses using [JSON-LD](https://www.w3.org/TR/did-core/#bib-json-ld) \(though other compatible graph-based data formats could be used\).
{% endhint %}

### Document storage

The ixo Network maintains a distributed registry of entities, which consists of DID:DDO pairs. An entity DID does not change, but the DDO record can be modified. 

All changes to the DDO are permanently stored and cannot be erased. Therefore, the information contained within a DDO on a public network must not contain any private or personal identifier data. For this reason \(and to reduce the replicated data storage load on the network\), the bulk of the descriptive content relating to an entity is stored "off-chain". 

As the default, ixo uses IPFS for off-chain document storage to be persistent and available. Document data may stored in IPFS may be either encrypted or unencrypted, depending on the preference of the DID controller. Off-chain objects that form part of the DDO are by default referenced in the DDO using [Content Identifiers \(CID\)](https://docs.ipfs.io/guides/concepts/cid/), which enable the data to be validated and locates the content file without any dependancies on URL paths that tend to break or become unavailable over time.

{% hint style="info" %}
Learn more about IPFS and content addresses \(CID\).
{% endhint %}

###  Document Objects

ixo Documents are compiled using a logical structure that can be accessed through standard API interfaces. This builds on the principles of the [Document Object Model](https://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113/introduction.html) \(DOM\), which is a core internet standard from W3C.

The generic structure of an ixo document has 3 sections:   

1. **Header section** which contais the document metadata.
2. **Page section** which contains public descriptive content about the entity, with a content-addressable link to off-chain document content \(which may be clear-text or encrypted\).  
3. **Core properties** which contains objects for:

* Identifiers
* Public Keys
* Authentication
* Authorisation and delegation
* Service endpoints
* Cryptographic proofs

See the technical specification \[insert link\] for these document objects.

{% hint style="warning" %}
A [DID](https://www.w3.org/TR/did-core/#dfn-decentralized-identifiers) and [DID document](https://www.w3.org/TR/did-core/#dfn-did-documents) do not inherently carry any [PII](https://en.wikipedia.org/wiki/Personally_identifiable_information) \(personally-identifiable information\).
{% endhint %}

### Document versioning

When a Document is created on an ixo protocol network, this produces a Genesis Record in the blockchain registry.

ixo Documents can only be updated following protocol rules:

1. A document update is only valid if it is added to the Document chain, which is an append-only log stored in an ixo protocol blockchain database.
2. To add an update to the document chain, a valid message must be submitted to the blockchain, which is signed by the controller of the DID for the entity.
3. The \`documentupdate\` message must contain a CID pointer to the previous record as `prev`, a patch containing the update to the document as `content`, and an encoded signature.

{% hint style="info" %}
Updates to this specification may in future be compatible with the [Ceramic Protocol](https://github.com/ceramicnetwork).
{% endhint %}



