---
stoplight-id: g5ozqwl9wecxt
---

# Implementing-dMRV

This guide describes how to deploy and manage decentralized digital Measurement, Reporting, and Verification (dMRV) for clean cooking programs using the Emerging Platform capabilities. It emphasizes real-time data capture, robust protocol configuration, and cryptographic verification—approaches that surpass conventional paper-based or survey-driven methods in accuracy, transparency, and trust.

## 1. Why IXO dMRV is Different
Unlike traditional MRV processes that often depend on manual reporting, intermittent sampling, or retrospective surveys, the IXO dMRV approach is:
- Real-Time: Leverages IoT or smart device data for continuous measurement.  
- Trust-Enhanced: Cryptographic proofs ensure authenticity, while the distributed ledger provides an immutable audit trail.  
- Efficient & Scalable: Protocol-based architecture lets developers plug in new projects quickly, enabling automated data validation and streamlined integration with recognized standards like Gold Standard.

## 2. Overview of the Methodology
The IXO dMRV system aligns with the Gold Standard Methodology for Metered & Measured Energy Cooking Devices (MMECD) and the project-specific Mitigation Activity Design Document (MADD) or Project Development Document (PDD). This methodology:
- Applies to modern cooking devices (biomass pellets, induction cookers, electric pressure cookers, metered LPG, etc.) that can log usage metrics (kWh, fuel consumption, operating times).  
- Ensures GHG emission reductions and additional SDG indicators are accurately tracked and readily auditable.  

### Key Principles
* Metering & Logging: Device-integrated sensors capture consumption in real time.  
- Data Integrity: Device-level usage data is cryptographically secured and linked to device DIDs on the blockchain.  
- Verification Workflow: Oracles and accredited auditors validate that consumption data meets the methodology requirements outlined in the MADD/PDD.

## 3. Configuring Projects with Protocols
In the IXO ecosystem, a “Protocol” encodes the operational and verification requirements of a particular project type. Here’s how to configure a clean cooking initiative:

### 3.1 Create or Reuse a Protocol
- Begin with an existing “Clean Cooking Protocol” that defines default fields and data flows (e.g., fuel usage logs, cooking sessions, emission factors).  
- If a relevant Protocol does not exist, create one. Customize required device attributes, usage thresholds, and verification rules per the MMECD or your PDD.

### 3.2 Adapt the Protocol to Your MADD/PDD
- Integrate baseline emission factors, reporting frequency, and any project-specific constraints (e.g., calibration intervals).  
- Align the Protocol with local regulations or additional standards where necessary.

### 3.3 Deploy the Protocol
- Instantiate the Protocol as a unique domain for your clean cooking project.  
- Assign each participating device a Digital Identifier (DID).  
- Register Oracles or other verification entities authorized to validate device data.  
- Configure rules for data submission (e.g., minimum batch size, allowable offline periods).

## 4. MRV Workflow in Practice

### 4.1 Measurement (Data Ingestion)
- Smart cooking appliances generate time-stamped usage logs (electricity consumption, fuel flow, temperature, etc.).  
- Data streams into the Emerging Platform via secure IoT pipelines or batch uploads.  
- Each record is cryptographically signed, hashed, and linked to the corresponding device DID.

### 4.2 Reporting (Data Aggregation)
- The platform aggregates records into claims relevant to the selected methodology and Protocol.  
- Automated or user-triggered processes calculate emission reductions, referencing baseline values and usage metrics.  
- Reports are formatted to match certification requirements (e.g., for Gold Standard submissions).

### 4.3 Verification (Data Validation)
- Oracles and/or independent auditors compare recorded metrics against MADD/PDD baselines.  
- Upon successful validation, verified claims become “verifiable credentials” stored on the blockchain.  
- Any anomalous data—such as excessive consumption spikes or prolonged device inactivity—automatically flags for deeper review.

## 5. Best Practices for Developers

### 5.1 Align IoT Integrations with Protocol Guidelines
Ensure your devices or data ingestion pipelines capture all required fields (e.g., timestamp, consumption type, device ID). Include fallback options for areas with poor network coverage (e.g., offline buffering).

### 5.2 Use the IXO Credential Framework
Issue tamper-evident verifiable credentials for each finalized claim, creating a transparent record for auditors, carbon credit buyers, or market regulators.

### 5.3 Manage Protocol Versions
Keep track of methodology updates, new hardware integrations, or adjusted baselines. Each Protocol version should reference how it differs from the last so that historical data remains valid and auditable.

### 5.4 Store Data Efficiently
While key transaction details (e.g., hashes, signatures) reside on-chain for immutability, large sensor datasets can remain off-chain. Always hash these off-chain files and record the hashes on-chain for data integrity.

### 5.5 Plan for Ongoing Security & Scale
- Rotate credentials and manage roles to limit potential exploits.  
- Configure appropriate governance for Oracles, ensuring their incentives align with honest data validation.  
- Scale node infrastructure and data pipelines as your project grows, maintaining consistent performance.

## 6. Conclusion
By combining real-time device telemetry, cryptographic data integrity, and protocol-driven workflows, the IXO dMRV approach for clean cooking projects delivers robust measurement, transparent reporting, and verifiable outcomes. Developers can efficiently adapt Protocols to reflect MADD/PDD nuances, ensuring compliance with recognized standards like the Gold Standard and boosting confidence in the reported climate impact. This system outperforms conventional MRV methods by minimizing manual intervention, reducing errors, and strengthening trust through decentralization—all critical factors for scaling modern energy cooking programs that meaningfully contribute to global emission reduction targets.
