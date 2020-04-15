---
description: Guideline for developing and displaying content on the Internet of Impact
---

# Create or view a Document

## Document standards

The purpose of documents in the Internet of Impact is to record information in a stateful way. The ixo protocol standard is that a document must be:

1. Verifiable
2. Attributable
3. Semantically interoperable
4. Univeral addressable
5. Human-readable
6. Machine-readable
7. Non-repudiable
8. Tamper-resistant
9. Persistently available
10. Private by design

## Document types

The ixo protocol defines a set of standard document types, which are used as building-blocks. 

### 1. DID Document \(DDO\) type

Each identifiable subject in the Internet of Impact has a Decentralised Identifier \(DID\). A specific format of document is associated with a DID, which is described as the DID Document \(DDO\). This is based on a specification from the W3C.

{% hint style="info" %}
The W3C describes a DID Document as "A set of data describing the [DID subject](https://www.w3.org/TR/did-core/#dfn-did-subjects), including mechanisms, such as public keys and pseudonymous biometrics, that the [DID subject](https://www.w3.org/TR/did-core/#dfn-did-subjects) can use to authenticate itself and prove their association with the [DID](https://www.w3.org/TR/did-core/#dfn-decentralized-identifiers). 

A DID document might also contain other [attributes](https://en.wikipedia.org/wiki/Attribute_%28computing%29) or claims describing the subject. These documents are graph-based data structures that are typically expressed using \[[JSON-LD](https://www.w3.org/TR/did-core/#bib-json-ld)\], but can be expressed using other compatible graph-based data formats.
{% endhint %}

The following DDO document subjects are defined in the ixo context:

* Cell document
* Project document
* Oracle document
* Bond document
* Data Asset document

A generic template \(in [JSON Template standard](https://tools.ietf.org/html/draft-jonas-json-template-language-01) format\) for each of these documents is currently maintained in Github under custodianship of the ixo Foundation.

The generic structure of an ixo protocol DID Document is illustrated below.

\[insert illustration\]

1. **Document Page** is the information which is displayed to an end-user. This uses standard Markdown Format for styling and to embed media into the page. See the Format a Page guide.

### 2. Claims document type

Claims are a high-definition data object which encodes information in a way that is portable, self-declarative and verifiable. Claims comply with the document standards by implementing the following features:

* Subjects are identified in a way that can be authenticated, using a DID.
* A schema context is declared, which resolves the claim data to a set of standard semantic definitions.
* An issuer is identified and authenticated, using a DID.
* The claim is cryptographically verifiable by its hash value and signatures.
* The claim object is content-addressable by its hash value \(using the IPLD specticification\).

The following claims categories are defined in the ixo context:

* Identity claim \(credential\)
* Impact claim
* Evaluation claim
* Dispute claim
* Transaction claim

A generic template \(in [JSON Template standard](https://tools.ietf.org/html/draft-jonas-json-template-language-01) format\) for each catgory of claims is currently maintained in Github under custodianship of the ixo Foundation.

The basic structure of an ixo protocol Claim is illustrated below.

\[insert illustration\]

## Viewing documents

### Verifiable displays





