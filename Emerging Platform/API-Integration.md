---
stoplight-id: 0u6gcad8tyblz
---

# API-Integration

### 9.1 Claim Submission
Use `POST /v1/claims` to submit new claims to the platform.

#### Fuel Purchase Example
```json
{
  "type": ["VerifiableCredential", "FuelPurchaseCredential"],
  "issuer": "did:ixo:entity:distributor-id",
  "credentialSubject": {
    "householdId": "did:ixo:entity:household-id",
    "paymentIdentifier": "MP220809.1234.H47041",
    "paymentDateTime": "2022-08-09T12:34:00Z",
    "devices": ["did:ixo:entity:device-id-1"]
  }
}
```

### 9.2 Household Management
Use `POST /v1/households` to register new households and link associated devices.

```json
{
  "householdMetadata": {
    "geographicLocation": "District XYZ",
    "densityClassification": "Medium"
  },
  "customers": [
    {
      "id": "did:ixo:entity:customer-id-1",
      "devices": [
        {
          "deviceId": "did:ixo:entity:device-id-1",
          "technology": "BiomassPellets",
          "vendor": "Company A",
          "serialNumber": "SN12345"
        }
      ]
    }
  ]
}
```

