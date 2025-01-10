---
stoplight-id: zj20b6m8odcxm
---

# Verifiable Claims

This guide will walk you through implementing Verifiable Claims using the Emerging Platform.
## Overview

Verifiable claims enable digital Measurement, Reporting, and Verification (dMRV) of outcomes from modern energy cooking activities.

A Verifiable Claim is a cryptographically secure statement about a fact or attribute that is issued and cryptographically signed by a trusted entity. These claims are structured as data items linked to a specific domain or entity, providing tamper-proof evidence of events, activities, or states—such as the usage of a device, delivery of goods, or achievement of an impact goal. 

Verifiable Claims leverage the latest web standards (W3C Verifiable Claims and Credentials) to ensure authenticity, integrity, and interoperability. This enables remote monitoring and decentralized verification without having to rely on central authorities and top-down processes. Verifiable Claims dynamically update a domain’s state and play a critical role in establishing trust within the Emerging Platform ecosystem, by assuring [data integrity](Emerging Platform/Data-Integrity.md). 

The main types of Verifiable Claims relevant to the Emerging Platform ecosystem include:

### Emission Reduction Claims
These claims are fundamental to the platform's carbon credit generation process:
- **Actual Energy Consumption**: Claims based on metered usage of modern cooking devices, such as electric, LPG, biogas, or advanced biomass pellet stoves.
- **Avoided Traditional Fuel Use**: Claims estimating the amount of traditional cooking fuel (e.g., firewood, charcoal) avoided due to the use of modern cooking devices.
- **Carbon Emission Reductions**: Claims quantifying the greenhouse gas emissions reduced by switching to clean cooking methods.

### Device-Related Claims
- **Device Installation**: Claims verifying the installation and activation of modern energy cooking devices in households.
- **Device Usage**: Claims tracking the actual usage patterns of clean cooking appliances.
- **Device Performance**: Claims related to the efficiency and effectiveness of the cooking devices.

### Fuel-Related Claims
- **Fuel Purchase**: Claims recording the purchase of sustainable fuel, such as biomass pellets.
- **Fuel Consumption**: Claims measuring the amount of clean cooking fuel used (e.g., biomass pellets, LPG, biogas, electricity).

### Social and Economic Impact Claims
- **Health Improvements**: Claims related to reduced exposure to indoor air pollution.
- **Time Savings**: Claims quantifying time saved by using modern cooking methods.
- **Economic Benefits**: Claims related to cost savings or income generation from clean cooking activities.

### Environmental Impact Claims
- **Deforestation Reduction**: Claims estimating the reduction in forest degradation due to decreased firewood usage.
- **Biodiversity Protection**: Claims related to the positive impacts on local ecosystems.

### User-Related Claims
- **User Onboarding**: Claims verifying the registration and onboarding of households to modern energy cooking services.
- **User Training**: Claims related to the training and education of users on clean cooking practices.
- **User Satisfaction**: Claims capturing feedback and satisfaction levels of clean cooking device users.

### Financial Claims
- **Payment Transactions**: Claims recording payments for fuel and related services.
- **Carbon Credit Issuance**: Claims related to the generation and issuance of carbon credits.
- **Revenue Distribution**: Claims tracking the distribution of proceeds from carbon credit sales.

These various types of claims, when processed and verified through the IXO Emerging Platform, contribute to a comprehensive and accurate representation of the impacts of modern energy cooking projects. The platform's use of digital technologies and real-time data collection ensures high integrity and transparency in the monitoring, reporting, and verification process.


# Technical Specification

## Overview
Verifiable Claims: A Foundation for Trusted Data in the Internet of Impact

Verifiable Claims are the cornerstone of all identified data objects within the Internet of Impact ecosystem. These claims enable the encoding of high-definition data with robust features that ensure security, trust, and interoperability. Key characteristics of Verifiable Claims include:
- Decentralized Identifiers (DIDs): Claims are resolvable to DIDs, ensuring verifiable ownership and authenticity
- Linked-Data Contexts: Ontology-based data models provide semantic clarity and enhance machine-readable interoperability
- Cryptographic Verifiability: Claims are cryptographically signed to guarantee data integrity and prevent tampering
- Content Addressability: Claims are referenced via unique hashes, ensuring their data is immutable and reliably retrievable
- Authenticated Relationships: Both the subject and issuer of a claim are cryptographically authenticated, enabling secure and trusted data exchanges

By integrating these capabilities, Verifiable Claims empower decentralized systems to operate with high assurance, fostering trust and transparency across the Internet of Impact.

## Claim Structure
A Verifiable Claim in IXO consists of the following components:

- **Claim object**
- **Data model**  
- **JSON Schema for validation**
- **Claim signature**

### Claim Object
The claim object contains the core data payload, typically structured as JSON-LD. For example:

```json
{
  "@context": "https://www.w3.org/2018/credentials/v1",
  "id": "http://example.edu/credentials/3732",
  "type": ["VerifiableCredential", "AlumniCredential"],
  "issuer": "https://example.edu/issuers/14",
  "issuanceDate": "2010-01-01T19:23:24Z",
  "credentialSubject": {
    "id": "did:example:ebfeb1f712ebc6f1c276e12ec21",
    "alumniOf": "Example University"
  }
}
```

### Data Model 
The data model defines the schema and semantics for the claim. IXO uses JSON-LD contexts to provide semantic meaning.

The relevant data models are:
- [**Fuel Purchase Claims**](../../models/Fuel-Purchase-Claim-Schema.json): Claims recording the purchase of sustainable fuel, such as biomass pellets.
- [**Carbon Emission Reductions Claims**](../../models/Certified-Emissions-Reduction.json): Claims quantifying the greenhouse gas emissions reduced by switching to clean cooking methods.
- [**Verifiable Emission Reductions Claims**](../../models/Verified-Emissions-Reduction.json): Claims facilitated by the Causal AI Oracle using Fuel Purchase and Carbon Emission Reductions Claims as input.

### JSON Schema
A JSON Schema is used to validate the structure of the claim object. For example:

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "@context": {
      "type": "string"
    },
    "id": {
      "type": "string"
    },
    "type": {
      "type": "array",
      "items": {
        "type": "string"
      }
    },
    "issuer": {
      "type": "string"
    },
    "issuanceDate": {
      "type": "string",
      "format": "date-time"
    },
    "credentialSubject": {
      "type": "object"
    }
  },
  "required": ["@context", "id", "type", "issuer", "issuanceDate", "credentialSubject"]
}
```
