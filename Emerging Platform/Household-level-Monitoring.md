---
stoplight-id: h7f87kzqsnbpa
---

# Household-level-Monitoring

## Introduction

Household-level monitoring aggregates data from one or more cooking devices used by a family or dwelling. Rather than tracking each device in isolation, this approach ensures a holistic view of how the household’s collective cooking practices influence fuel consumption and emissions. 

By using the Emerging Platform’s decentralized identifiers (DIDs), verifiable credentials, and data orchestration tools, you can automate the measurement, reporting, and verification (MRV) of these activities while aligning with Mitigation Activity Design Documents, recognized standards and methodologies (Gold Standard for Metered & Measured Energy Cooking Devices).

## Key Components of the Architecture

1. **Household DID**  
   Each household is represented by a unique, decentralized identifier. All devices, claims, and verifications link back to the Household DID, ensuring consistency and traceability.

2. **Device DIDs**  
   Cooking appliances (e.g., electric pressure cookers, biomass stoves, or LPG burners) each have their own DID. This allows for cryptographically secure data signatures at the device level.

3. **Claims and Credentials**  
   A claim captures an activity or event (e.g., fuel purchase, device usage), while a credential is a verifiable digital document proving that claim is valid. This distinction enables strong traceability and trust.

4. **Oracle Services**  
   Oracles are specialized software entities (or modules) with domain-specific knowledge. They verify claims, detect anomalies, and can perform causal AI analysis to prevent double-counting and ensure accurate emission reduction calculations.

5. **Immutable Data Store**  
   Critical metadata (e.g., cryptographic hashes, usage summaries, verification statuses) are anchored on a blockchain-based directed acyclic graph (DAG). Large telemetry data may reside off-chain, with references and hashes on-chain for immutability.

## Setting Up a Household for dMRV

### Registration

1. **Create a Household DID**  
   - Use the platform’s DID registration endpoint to generate a unique identifier for the household.  
   - Store any metadata (e.g., location, population, technology preferences).

2. **Associate Customer or Resident Profiles**  
   - Optionally, link individual customers or household residents to the household.  
   - This helps track user-level interactions and device ownership.

3. **Schema Example (JSON Payload)**

```json
{
  "householdMetadata": {
    "geographicLocation": "District XYZ",
    "densityClassification": "Medium"
  },
  "customers": [
    {
      "id": "did:ixo:entity:customer-id-1",
      "devices": []
    }
  ]
}
```


## Device Integration and Data Collection

### Device Onboarding

• **Device DID Creation**: Every stove or cooktop must be registered with the platform. This includes specifying the device model, serial number, and fuel type.  
• **Sensor Calibration and Configuration**: Ensure that the cooking device’s sensors (e.g., temperature, fuel flow, electricity usage) meet the accuracy and reporting guidelines defined by the methodology.

## Data Ingestion Architecture

1. **IoT Connectivity**  
   - Devices periodically send telemetry to the platform (e.g., via MQTT, HTTP, or LoRaWAN gateways).  
2. **Edge or Mobile App Logging**  
   - In areas without reliable connectivity, mobile apps can store data offline and sync it to the platform when a connection is available.
3. **Cryptographic Signatures**  
   - Each measurement is digitally signed with the device’s private key.  
   - The platform verifies these signatures, ensuring no tampering in transit.

### Claims Creation

After each measurement cycle or transaction (e.g., fuel delivery):
1. **Claim Payload**  
   - Basic attributes: device ID, timestamp, usage metrics (e.g., burn time, fuel consumed).  
   - Sign with the device’s private key.  
2. **Household Association**  
   - Link each claim to the Household DID for aggregated analytics.

## Reporting and Aggregation at Household Level

### Household Credential

Once claims accumulate, the household can receive an updated credential summarizing its consumption and fuel-switching activities:
• **Credential Subject**: The household (via Household DID)  
• **Embedded Claims**: A list of usage claims or references to them (instead of duplicating raw telemetry data).

```json
{
  "@context": ["https://www.w3.org/2018/credentials/v2"],
  "type": ["VerifiableCredential", "HouseholdReportCredential"],
  "issuer": "did:ixo:entity:oracle-id",
  "issuanceDate": "2025-01-09T10:00:00Z",
  "credentialSubject": {
    "id": "did:ixo:entity:household-id",
    "reportPeriod": {
      "startDate": "2025-01-01",
      "endDate": "2025-01-31"
    },
    "claimsReferences": [
      "claim-id-1",
      "claim-id-2"
    ],
    "aggregatedUsage": {
      "fuelTypeLPG_kWhEquivalent": 25,
      "fuelTypeBiomassPellets_kg": 40
    }
  }
}
```

### Stove Stacking and Fuel Switching

When multiple devices are linked to a household, the platform uses these references to:
• **Detect Overlaps**: Identify if devices of different fuel types operated concurrently.  
• **Prevent Double-Counting**: The Oracle cross-checks usage from multiple stoves to ensure the baseline emissions offset is only claimed once for the same cooking needs.

## Verification Workflows

### Oracle-Based Analysis

1. **Data Validation**  
   - The Oracle retrieves all usage claims from the household.  
   - Compares timestamps, quantities, and device types with expected patterns (e.g., the MMECD methodology’s standards).

2. **Anomaly Detection**  
   - Flags contradictory or implausible claims (e.g., more hours of cooking logged than possible in a day).  
   - Identifies suspicious fuel purchase or usage intervals that don’t align with delivery logs.

3. **Causal AI**  
   - If stove-stacking is detected, a causal model estimates each device’s impact versus a counterfactual scenario without that device.  
   - Helps accurately attribute emission reductions to each device-fuel combination.

###  Manual or Third-Party Auditing

• **External Auditors**  
  - Some projects or registries (e.g., Gold Standard) require third-party verification. Auditors can pull verifiable credentials from the platform, check relevant cryptographic proofs, and confirm sensor accuracy.  
• **On-Site Inspections**  
  - Auditors may physically inspect a subset of stoves for calibration checks, ensuring device data is reliable.

## Emission Reduction Calculation

The specfic calculations for each project are based on the approved parameters and procedures described in the Mitigation Activity Design Document (MADD) or Project Design Document (PDD).
This generally follows the following patterns:

### Baseline vs. Actual Emissions

1. **Baseline Emissions**: Estimate the household’s emissions using its traditional cooking fuels (e.g., wood, charcoal).  
2. **Actual Emissions**: Aggregate the real-time usage data from the new, cleaner devices.  
3. **Reduction** = Baseline – Actual

### Stove Stacking Considerations

• **Partial Fuel Switch**  
  - If the household is using both LPG and biomass, the platform’s data integration keeps a record of exactly how much of each fuel was used in a given period.  
• **Weighted Emission Factors**  
  - Each device or fuel source has a known emission factor. The platform automatically applies these to the usage logs, summing the total emissions for the period.

#### Pseudocode for Emission Calculations

```pseudo
function calculateHouseholdEmissions(householdId, startDate, endDate):
    // Step 1: Fetch all claims for the household in the date range
    claimsList = getClaims(householdId, startDate, endDate)

    // Step 2: Aggregate usage by device-fuel type
    usageMap = {}
    for claim in claimsList:
        deviceType = claim.deviceType
        fuelConsumed = claim.fuelConsumed
        usageMap[deviceType] += fuelConsumed

    // Step 3: Compute emissions from each device-fuel
    totalEmissions = 0
    for deviceType in usageMap:
        factor = getEmissionFactor(deviceType)
        totalEmissions += usageMap[deviceType] * factor

    return totalEmissions
```

### Stove Stacking in Action: Example Workflow

1. **Device 1 (LPG Stove)** logs 2 hours of cooking on 2025-01-10.  
2. **Device 2 (Biomass Pellets Stove)** logs 3 kg of pellets used on the same date.  
3. **Household Aggregation**: The platform sees both sets of claims under the same household ID.  
4. **Analysis**: The Oracle checks whether these cooking sessions overlapped in time to avoid double-counting the same cooking needs.  
5. **Emission Reduction**: The Oracle or causal AI model splits the total reduction between the two devices, each relative to its baseline scenario.


## API Endpoints and Integration

### Household Management
- `POST /v1/households`  
  - Registers a new household or updates metadata.  

### Claim Submission
- `POST /v1/claims`  
  - Accepts new claims (e.g., usage logs, fuel purchase).  

### Oracle Query
- `POST /dmrv/analysis`  
  - Trigger an analysis run for a specified period or set of claims.  

### Credential Issuance
- `POST /v1/credentials`  
  - Issues a verifiable credential once claims pass Oracle validation.

## Best Practices

1. **Standardized Protocols**  
   - Adopt existing protocols (e.g., a “Clean Cooking Protocol”) that define data schemas, usage intervals, and emission factors to avoid custom logic for each project.  
2. **Fallback Options**  
   - In limited-connectivity scenarios, allow devices or mobile apps to buffer data. On reconnection, the entire data set can be batch-submitted for verification.  
3. **Security**  
   - Rotate device keys periodically.  
   - Employ robust authentication to ensure only authorized actors can submit or modify claims.  
4. **Governance and Auditing**  
   - Keep an immutable on-chain record of all updates to device configurations and Oracle validations.  
   - Conduct routine system checks for data consistency.  
5. **Scalability**  
   - Use containerization or cloud auto-scaling for high-volume projects.  
   - Employ message queues for asynchronous telemetry processing.


## Conclusion

Household-level monitoring on the Emerging Platform provides a robust, verifiable, and scalable framework for clean cooking dMRV. By registering households and their devices under DIDs, collecting real-time sensor data, and employing Oracle-based validation—enhanced by causal AI—the system accurately attributes emission reductions, even under complex stove-stacking scenarios. This holistic approach not only bolsters credibility among stakeholders and carbon registries but also yields actionable insights for program improvement.

By following the steps above, developers and project implementers can ensure transparent, accurate, and efficient MRV of modern energy cooking activities, helping accelerate the global transition to cleaner, more sustainable cooking solutions.