---
stoplight-id: tfoyzkf9nkdgr
---

# Verifiable Claims
This guide will walk you through implementing Verifiable Claims using the IXO protocols and Spatial Web platform.
## Overview
The Emerging Platform for Modern Energy Cooking, built on the IXO infrastructure, enables various types of claims relevant to clean cooking implementation. These claims are essential for digital Measurement, Reporting, and Verification (dMRV) of outcomes from modern energy cooking activities. The main types of claims include:

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
- **Fuel Consumption**: Claims measuring the amount of clean cooking fuel used (e.g., LPG, biogas, electricity).
- **Fuel Purchase**: Claims recording the purchase of sustainable fuel, such as biomass pellets.

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
Verifiable Claims are the foundation for all identified data objects in the Internet of Impact. They allow encoding high-definition data with the following key characteristics:

- Resolution to decentralized identifier keys (DIDs)
- Linked-data contexts for resolving ontologies  
- Cryptographic verifiability
- Content addressability
- Cryptographic authentication of subject and issuer

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

### Claim Signature
The claim is cryptographically signed by the issuer to ensure authenticity and integrity.

### Implementation

To implement Verifiable Claims in your application, refer to the IXO Spatial Web [implementation guides](../../Implementation-Guides/Implementation-Guides-Overview.md).

#### Best Practices
- Use standardized claim schemas where possible to ensure interoperability
- Implement proper key management for DIDs used to sign claims
- Validate claims against their JSON Schema before processing
- Store claims securely, preferably using decentralized storage like IPFS

#### Conclusion
By following this guide, you can implement Verifiable Claims in your application using the IXO protocols and Spatial Web platform. This enables secure, verifiable data exchange in the Internet of Impacts ecosystem.


