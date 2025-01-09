---
stoplight-id: v0f0zl44gtl42
---

# Digital-Certification

# Digital Certification of ITMOs

## 1. Introduction

This documentation describes how to implement Internationally Transferred Mitigation Outcome (ITMO) certificates using the W3C Verifiable Credential (VC) standard. It also explains how the accompanying JSON-LD context (the "itmo" context) helps define and interpret domain-specific properties relevant to Article 6.2 of the Paris Agreement. By following this schema, developers can create machine-verifiable, tamper-resistant ITMO certificates for carbon trading or cross-border climate initiatives.

## 2. Why Use Verifiable Credentials for ITMOs?

### Trust and Transparency
Verifiable Credentials rely on cryptographic signatures to prove authenticity and detect tampering. This ensures that ITMO data, such as NDC quantification or authorization references, is trustworthy and resistant to manipulation.

### Global Interoperability
Because the W3C Verifiable Credential format is widely recognized, any platform supporting VCs can parse, validate, and exchange these ITMO certificates. This fosters international collaboration and harmonizes data formats for Article 6.2 compliance.

### Modular and Extensible
The JSON-LD approach allows different stakeholders (e.g., project developers, governments, registries) to add or update properties without breaking interoperability. Additional contexts can be layered on to capture extra information as policies evolve.

### Fine-Grained Control Over Privacy
VCs support selective disclosure, letting issuers or holders share only the necessary claims. In ITMO transactions, certain sensitive details (e.g., underlying financial arrangements) can be omitted if only emissions or authorization data is required.

## 3. Schema Overview

The ITMO Credential Schema is an extension of the W3C Verifiable Credentials data model. Each ITMO certificate has core properties:

* **issuer** (the entity or Party issuing the VC)
* **issuanceDate** and **expirationDate**
* **credentialSubject** (the main body of ITMO-related data)
* **evidence** (optional supporting documents)
* **proof** (a cryptographic signature verifying authenticity)

Within `credentialSubject`, ITMO-specific fields are grouped into sub-sections, such as `authorizationInfo`, `ndcQuantification`, `correspondingAdjustments`, and `environmentalIntegrity`. These hold crucial details like references to authorizing entities, greenhouse gases covered, and environmental integrity metrics.

## 4. JSON-LD Context Explanation

### Purpose of the "itmo" Context

JSON-LD contexts map human-readable property names (e.g., `ndcReferenceLevel`) to IRIs (e.g., `itmo:ndcReferenceLevel`), ensuring consistency and machine-readable semantics across different systems. The "itmo" context file you host at a stable URL (e.g., `https://w3id.org/article6/itmo-context.jsonld`) contains definitions for properties such as:

* `authorizationReference`
* `ndcGHGs`
* `correspondingAdjustments`
* `mostRecentNationalInventory`

Each property includes `domainIncludes` and `rangeIncludes` statements referencing schema.org types, making it easier for implementers to validate data types and structures.

### Referencing the Context

In your ITMO credential, add the context URLs in the "@context" array. For example:

```json
"@context": [
  "https://www.w3.org/2018/credentials/v1",
  "https://w3id.org/security/suites/ed25519-2018/v1",
  {
    "itmo": "https://w3id.org/article6/itmo-context.jsonld"
  }
]
```

This ensures:

* The baseline W3C VC definitions are present
* Ed25519 cryptographic suite definitions are included
* ITMO-specific properties map to your "itmo" prefix

### How JSON-LD Processes the ITMO Fields

When a verifier or parser reads the credential, it looks up "itmo:authorizationReference" in the "itmo" context. The context file describes it as a rdf:Property with domain itmo:ITMOCredential, clarifying that authorizationReference is text used within a credential typed as ITMOCredential. JSON-LD tooling then interprets the meaning of the property, enabling a consistent, semantic understanding across systems.

## 5. Implementation Steps

### Creating an ITMO Credential

To create a valid ITMO credential:

1. **Prepare the Base Document**
   * Include required W3C VC fields
   * Add ITMO-specific context
   * Structure the `credentialSubject` data

2. **Add Required ITMO Fields**
   * Authorization information
   * NDC quantification data
   * Environmental integrity metrics

### Example ITMO Credential

```json
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "https://w3id.org/article6/itmo-context.jsonld"
  ],
  "type": ["VerifiableCredential", "ITMOCertificate"],
  "issuer": "did:example:123",
  "issuanceDate": "2024-03-15T00:00:00Z",
  "credentialSubject": {
    "id": "did:example:456",
    "authorizationInfo": {
      "reference": "AUTH-2024-001",
      "issuingParty": "Country A"
    }
  }
}
```

## 6. Validation and Verification

### Technical Validation

Implementers should verify:

* **Schema Conformance** - Ensure all required fields are present
* **Context Resolution** - Verify all JSON-LD contexts resolve correctly
* **Signature Verification** - Validate the cryptographic proof

### Business Rules Validation

Check that:

* All required ITMO-specific fields are present
* Values conform to Article 6.2 requirements
* Environmental integrity criteria are met

## 7. Best Practices

### Security Considerations

* Use strong cryptographic keys
* Implement proper key management
* Regular security audits
* Monitor for compromised credentials

### Privacy Considerations

* Implement selective disclosure when possible
* Use minimal disclosure principle
* Consider data retention policies
* Comply with relevant privacy regulations

## 8. Conclusion

By leveraging the W3C Verifiable Credential standard and the specialized JSON-LD context for ITMOs, developers can produce highly reliable, machine-verifiable records of climate action. This approach integrates seamlessly with blockchain-based registries, decentralized identifiers, and existing carbon accounting platforms, while remaining adaptable to future policy and technology changes.

Developers using this schema will enjoy:

• Consistency with established global standards.  
• Enhanced accuracy and traceability of ITMO data.  
• Modular design enabling easy extension for new environmental or financial metrics.  

For questions or contributions, consult your platform’s documentation on VC issuance and verification, or get involved with the broader Verifiable Credentials and Article 6.2 communities working to strengthen climate data interoperability.

## 9. References

* [W3C Verifiable Credentials Data Model](https://www.w3.org/TR/vc-data-model/)
* [Article 6.2 of the Paris Agreement](https://unfccc.int/process/the-paris-agreement/cooperative-implementation)
* [JSON-LD 1.1](https://www.w3.org/TR/json-ld11/)


