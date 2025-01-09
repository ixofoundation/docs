---
stoplight-id: xmebkzp1z1s5j
---

# ITMO Credential Data Model

Below is a first-draft version of the proposed ITMO Certificate Verifiable Credential data model.

```json
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "https://w3id.org/security/suites/ed25519-2018/v1",
    {
      "itmo": "https://w3id.org/article6/itmo-context.jsonld",
      "prov": "http://www.w3.org/ns/prov#"
    }
  ],
  "id": "urn:uuid:ceb12e68-2efd-4c9e-a4df-343bbfb11b7a",
  "type": [
    "VerifiableCredential",
    "ITMOCredential"
  ],
  "issuer": "did:ixo:entity:a1fcead81eab2f1158a726597d872413",
  "issuanceDate": "2023-07-12T12:06:32.104Z",
  "expirationDate": "2030-12-31T23:59:59Z",

  "credentialSubject": {
    "id": "did:ixo:entity:4e32697c7c2c74f4fac48e4d1d5628cd",
    "itmo:authorizationInfo": {
      "itmo:authorizationReference": "AUTH-REF-CC-LEGACY",
      "itmo:cooperativeApproachDuration": "2022-08-09T12:34:00Z/2022-09-09T10:49:00Z",
      "itmo:expectedMitigationOutcomes": {
        "2022": 5000
      },
      "itmo:participatingParties": [
        "Zambia"
      ],
      "itmo:authorizedEntities": [
        "did:ixo:entity:b3839c8bccf7ecff3cb6822869bb0d81"
      ]
    },
    "itmo:ndcQuantification": {
      "itmo:ndcSectors": [
        "Residential",
        "HouseholdEnergyUse"
      ],
      "itmo:ndcSources": [
        "BiomassFuelCombustion"
      ],
      "itmo:ndcGHGs": [
        "CO2",
        "CH4",
        "N2O"
      ],
      "itmo:ndcTimePeriods": [
        "2022"
      ],
      "itmo:ndcReferenceLevel": 1000,
      "itmo:ndcTargetLevel": 900,
      "itmo:ndcQuantificationTonnesCO2e": 100
    },
    "itmo:correspondingAdjustments": {
      "itmo:singleYearNDC": true,
      "itmo:multiYearNDC": false,
      "itmo:emissionsTrajectory": [
        1000,
        950
      ],
      "itmo:annualCorrespondingAdjustments": [
        50
      ],
      "itmo:averageAnnualITMOs": 50,
      "itmo:cumulativeAdjustments": 50
    },
    "itmo:environmentalIntegrity": {
      "itmo:environmentalIntegrityMetrics": [
        "CO2e"
      ],
      "itmo:ipccMethodologiesReference": "IPCC-2006-Guidelines",
      "itmo:otherNonGHGMetrics": [],
      "itmo:partyStatusUnderParis": true,
      "itmo:maintainedNDC": true,
      "itmo:trackingArrangements": [
        "https://example-registry.gov/tracking/ITMO_CleanCooking_Legacy"
      ],
      "itmo:mostRecentNationalInventory": "https://example-registry.gov/inventory/2022",
      "itmo:contributionToNDCImplementation": true
    }
  },

  "credentialSchema": {
    "id": "https://w3id.org/article6/schemas/itmo-vc.json",
    "type": "JsonSchemaValidator2018"
  },
  "credentialStatus": {
    "id": "https://example-registry.gov/status/ceb12e68-2efd-4c9e-a4df-343bbfb11b7a",
    "type": "CredentialStatusList2021"
  },
  "evidence": [
    {
      "id": "registry.example.org/6D5FA6521F06150F87FF42182F979527915CE83D82E4B1EB439F859AAFF1DBB7",
      "type": "BlockchainTransaction",
      "description": "Credits Transferred on the Impact Hub Registry"
    }
  ],

  "prov:wasGeneratedBy": {
    "id": "urn:uuid:IssuanceActivity-1234-5678",
    "type": "prov:Activity",
    "prov:startedAtTime": "2023-07-12T12:06:32.104Z",
    "prov:endedAtTime": "2023-07-12T12:06:32.104Z",
    "prov:wasAssociatedWith": "did:ixo:entity:a1fcead81eab2f1158a726597d872413",
    "prov:used": [
      {
        "id": "registry.example.org/6D5FA6521F06150F87FF42182F979527915CE83D82E4B1EB439F859AAFF1DBB7",
        "type": "prov:Entity"
      }
    ]
  },
  "prov:wasAttributedTo": "did:ixo:entity:a1fcead81eab2f1158a726597d872413",

  "proof": {
    "type": "Ed25519Signature2018",
    "created": "2023-07-12T12:06:32Z",
    "verificationMethod": "did:ixo:entity:a1fcead81eab2f1158a726597d872413#AbtJaG1pKif4pw34B5uKM6PXv9e3saSVjgF1kDpLMFhH",
    "proofPurpose": "assertionMethod",
    "challenge": "exampleChallenge",
    "domain": "example.org",
    "proofValue": "z3ZyQ..."
  }
}
```