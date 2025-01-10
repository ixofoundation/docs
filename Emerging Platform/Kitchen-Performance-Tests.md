---
stoplight-id: w0m1gvsy8rldg
---

# Kitchen Perfomance Tests


## Introduction

### What is a KPT?
A Kitchen Performance Test is a field-based method used to evaluate the amount of fuel consumed by a household over a given period under real-world conditions. KPTs usually span multiple days and account for local cooking practices, such as the number of meals, types of dishes, and variations in stove usage. By measuring actual fuel consumption, KPTs establish a baseline or confirm efficiency gains from new cooking devices.

### Why Integrate KPTs into dMRV?
- **Calibration**: KPTs provide on-the-ground insights, capturing behavior not easily observable via automated sensors alone.  
- **Methodology Alignment**: Recognized standards (e.g., Gold Standard MMECD) often allow or require KPT data for validation, especially when analyzing baseline fuels or usage patterns.  
- **Enhanced Credibility**: Combining KPTs with real-time IoT data can strengthen the certainty of reported emission reductions and improve auditor/regulator confidence.

## Architectural Overview

Below is a high-level view of how KPTs fit into the platform’s existing components:

1. **Household DID** – Each household conducting a KPT is registered as a unique decentralized identifier (DID).  
2. **Device DIDs** – Each stove (improved or traditional baseline) also has its own DID.  
3. **Claims & Credentials** – KPT results become structured claims, which can be issued as verifiable credentials once validated.  
4. **Immutable Ledger** – Essential KPT data (e.g., fuel used, usage duration) is anchored on-chain, ensuring no tampering.  
5. **Oracle Services** – Oracles validate KPT claims against field forms, sensor data, and baseline usage assumptions.

## Data Model for KPT Integration

### KPT Claim Structure
A KPT is generally a multi-day test. In the platform, KPT data is captured as one or more “KPT claims.” Each claim includes:

- **kptIdentifier**: Unique reference to a specific Kitchen Performance Test instance (e.g., “KPT-12345”).  
- **householdId**: Links the KPT to a household DID.  
- **devicesInvolved**: Array of device DIDs used during the test (e.g., baseline stove DID, improved stove DID).  
- **startDate / endDate**: Period covering the test duration.  
- **fuelMeasurements**: Daily or total fuel usage measurements, typically in kg for solid fuels or liters for liquid fuels.  
- **cookingSessions**: (Optional) Summaries of each cooking event if captured (e.g., type of meal, time spent).  
- **dataCollectors**: Individuals who conducted the test, possibly with their own DIDs for attribution.  
- **evidence**: References or attachments (photos, forms, calibration certificates).

#### Example JSON Payload (KPT Claim)

```json
{
  "@context": [
    "https://www.w3.org/2018/credentials/v2",
    {
      "kpt": "https://w3id.org/clean-cooking/kpt-context.jsonld"
    }
  ],
  "type": ["VerifiableCredential", "KPTCredential"],
  "issuer": "did:ixo:entity:kpt-auditor",
  "issuanceDate": "2025-01-10T09:00:00Z",
  "credentialSubject": {
    "id": "did:ixo:entity:household-id",
    "kptIdentifier": "KPT-12345",
    "startDate": "2025-01-05",
    "endDate": "2025-01-09",
    "devicesInvolved": [
      "did:ixo:entity:device-baseline",
      "did:ixo:entity:device-improved"
    ],
    "fuelMeasurements": {
      "day1": 3.2,
      "day2": 2.8,
      "day3": 3.0,
      "day4": 2.9,
      "total": 11.9
    },
    "dataCollectors": [
      {
        "collectorId": "did:ixo:entity:technician-id-1",
        "role": "FieldEnumerator"
      }
    ],
    "evidence": [
      "ipfs://QmevidenceformX12",
      "ipfs://QmhouseholdphotoABC"
    ]
  }
}
```

## KPT Implementation Workflow

### Pre-Test Setup
1. **Household & Device Registration**  
   - Confirm that the household DID and relevant device DIDs are registered in the platform.  
   - If an old baseline stove is being tracked, it should have its own DID and baseline characteristics (e.g., typical wood usage).

2. **KPT Protocol Configuration**  
   - Define a specialized “KPT protocol” or adapt an existing Clean Cooking Protocol to specify KPT data fields (fuelMeasurements, dataCollectors, etc.).  
   - This ensures consistent data capture across all KPTs within the platform.

### Field Data Collection
1. **Physical Measurement**  
   - Field technicians measure starting and ending fuel weights for each day, or track total consumption over the KPT period.  
   - They may also record cooking session data, weather conditions, or special events (e.g., celebrations that require extra cooking).  
2. **Offline Logging**  
   - In low-connectivity areas, data might be recorded in a mobile app or paper form. When connectivity is restored, these logs are submitted to the platform.

### Claim Submission
Once the test finishes:
1. **Compile KPT Results**  
   - Aggregate daily logs into a single claim or a series of claims, each referencing the same kptIdentifier.  
2. **Sign & Submit**  
   - The KPT data is cryptographically signed by the data collector or project manager.  
   - Submitted to the platform via a claim endpoint (`POST /v1/claims`).

## Verification and Validation

### Oracle Validation
- **Data Consistency**  
  - The Oracle checks for logic inconsistencies (e.g., day2 fuel usage can’t exceed day1 usage if devices or household size remain unchanged).  
  - Ensures that usage doesn’t conflict with any real-time sensor data from the improved stove, if available.  
- **Cross-Referencing**  
  - If the household also has IoT sensors, the Oracle compares sensor readings with reported KPT fuel consumption. If they diverge significantly, an alert is raised.  
- **Anomaly Detection**  
  - Large or unusual discrepancies trigger further scrutiny, possibly requiring additional documentation or field rechecks.

### Issuing a KPT Verifiable Credential
- **Credential Generation**  
  - Once validated, the Oracle (or designated verifier) issues a credential to confirm authenticity of the KPT results.  
- **On-Chain Anchoring**  
  - The KPT credential’s hash is stored on-chain in a DAG for immutability, while large attachments (like photos) may go to IPFS or another distributed file system.  

## Integrating KPT Data with Real-Time dMRV

### Baseline Emissions
KPT data can be used to refine or validate the baseline for households that have not yet switched to cleaner stoves. By measuring actual stove usage in situ, the platform calculates realistic pre-intervention fuel consumption rates.

### Ongoing Monitoring
Where IoT-enabled improved stoves are deployed:
- The KPT results serve as a reference benchmark.  
- Real-time sensor data (e.g., daily usage logs) is cross-checked against KPT-based baselines.  
- The platform updates or recalibrates the household’s baseline scenario if KPT reveals significant differences from previously assumed usage patterns.

### Stove Stacking Insights
Because a KPT may involve measuring multiple devices in parallel (e.g., a new improved cookstove plus a traditional backup stove), it can highlight stove stacking behaviors:
- The platform can detect partial or incomplete shifts to the cleaner stove.  
- Verified KPT results then feed into the Oracle’s causal analysis, preventing double-counting of emission reductions when multiple devices are in use.

## Emission Reduction Calculations with KPT Inputs

### Combining KPT and Automated Data
The platform can combine daily or event-based sensor data with KPT-based measurements:
- **KPT-Derived Factors**  
  - E.g., KPT might reveal that 1 kg of wood is used per meal, on average.  
- **Inferred Emissions**  
  - If sensor data from an improved stove indicates half the meals are cooked with the new device, the platform can estimate the baseline wood usage replaced.

#### Pseudocode for Emission Reduction
```pseudo
function computeEmissionReductions(householdId, kptId, improvedDeviceLogs):
    // 1. Retrieve KPT claims for the specified test
    kptData = getKPTData(householdId, kptId)
    baselineFuelConsumption = kptData.fuelMeasurements.total

    // 2. Get usage logs from improved device
    deviceUsage = getSensorLogs(improvedDeviceLogs)

    // 3. Calculate baseline emissions (e.g., baselineFactor is CO2e per kg of wood)
    baselineEmissions = baselineFuelConsumption * baselineFactor

    // 4. Calculate actual emissions from improved device
    actualEmissions = 0
    for usageRecord in deviceUsage:
        actualEmissions += usageRecord.fuelConsumed * improvedStoveFactor

    // 5. Emission reductions
    emissionReductions = baselineEmissions - actualEmissions
    return emissionReductions
```

## Reporting and Use of KPT Results

### Household-Level Reports
- The final KPT credential references the total fuel used by baseline vs. improved stoves.  
- This can be integrated into a HouseholdReportCredential, summarizing overall performance.

### Aggregation for Project-Wide Insights
- At scale, multiple KPT credentials feed into project-level dashboards.  
- Program managers or validators can compare KPT results across households or communities, identifying where the transition to improved cookstoves is most effective.

### Sharing with Carbon Registries
- For carbon offset programs (e.g., Gold Standard, Verified Carbon Standard), KPT results are often essential to demonstrate accurate baseline usage.  
- By providing a cryptographically verifiable KPT credential, project developers can streamline validation with third-party auditors.

## Governance and Quality Control

### Field Auditor Roles
- Certain KPT data collectors may hold special auditor roles in the platform.  
- Their digital signatures carry additional weight for verification, minimizing the risk of falsified data.

### Versioning and Protocol Updates
- Methodologies around KPT may evolve (new measurement approaches or adjusted baseline assumptions).  
- Maintain version-controlled KPT protocols. Each household’s KPT data references the specific protocol version in effect when the test was conducted.

### Dispute Resolution
- If an audit reveals potential inconsistencies, the platform can invalidate the KPT credential.  
- A new or corrected KPT claim can then be submitted, referencing the old claim for transparency.

## Best Practices and Recommendations

1. **Robust Training**  
   - Ensure enumerators and data collectors are well-trained in KPT procedures to reduce measurement errors.  
2. **Cross-Verification with Sensors**  
   - Whenever possible, pair KPT results with IoT logs to catch anomalies or questionable data entries.  
3. **Secure Offline Collection**  
   - Use mobile apps with tamper-proof logs and offline encryption for areas without internet connectivity.  
4. **Frequent Spot Checks**  
   - Conduct random surprise visits or additional short-term KPTs to verify long-term performance claims.

## Conclusion

Kitchen Performance Tests provide critical real-world data on stove and fuel usage, especially valuable for establishing baselines and confirming actual behavior in settings where sensor coverage may be incomplete. By integrating KPTs into the Emerging Platform, project developers gain:

- A verified record of household-level fuel consumption.
- Enhanced credibility for claimed emissions reductions.
- Ability to cross-check real-time data from improved stoves against on-the-ground measurements.

Through a unified system of DIDs, verifiable credentials, Oracle-based validation, and secure on-chain records, KPTs become an integral part of a robust, transparent dMRV process. This synergy between field-based testing and digital monitoring fosters greater trust among carbon markets, funding agencies, and the communities adopting cleaner cooking technologies.
