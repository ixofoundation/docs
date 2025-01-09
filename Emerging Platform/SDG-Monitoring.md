---
stoplight-id: o8z85zf41rlgb
---

# Monitoring SDG Outcomes

This technical guide describes how the Emerging Platform’s decentralized Measurement, Reporting, and Verification (dMRV) mechanisms capture and validate data for a range of Sustainable Development Goal (SDG) indicators. Each SDG indicator has unique parameters and data sources; however, the underlying approach—leveraging the Emerging Platform’s DID-driven architecture, verifiable claims, and Oracle-based validation—remains consistent.

## Overview

1. **Household, Entity, or Project DID**  
   - Every entity (e.g., household, business) is registered with a Decentralized Identifier (DID).  
   - All claims (e.g., fuel purchase, survey data) associate to these DIDs, ensuring traceability.

2. **Claims and Credentials**  
   - A claim is a data record stating something about an entity (e.g., total annual savings on cooking fuels).  
   - Once verified, claims are turned into verifiable credentials, which are cryptographically signed and stored or referenced on the Emerging Platform’s immutable ledger.

3. **Oracles**  
   - Automated or human-approved agents that validate the authenticity and consistency of claims.  
   - Oracles can check data from external APIs, sensor logs, survey forms, or partner databases.

4. **Ex-Post and Ex-Ante Data Collection**  
   - Ex-Ante evaluations: Data gathered at the start of the project or before an intervention (baseline).  
   - Ex-Post evaluations: Data collected after a defined interval (e.g., biannual surveys, annual audits).

5. **Integration with External Tools**  
   - The platform can ingest survey data, third-party monitoring reports, and GIS-based data for advanced indicators like air quality or fraction of non-renewable biomass.

## SDG Indicator Implementation

Below is a breakdown of each SDG indicator with the recommended technical approach for capturing, verifying, and reporting data on the Emerging Platform.

### SDG 1: No Poverty

**Indicator**: Annual USD amount saved on cooking fuels per household.  
**Parameter**: Household fuel expenditure (baseline vs. current).  
**Method**: Ex-Post analysis of fuel purchase claims validated by payment transactions.

#### Data Flow
1. **Household DID Registration**  
   - Each household is registered with a DID, linking them to fuel purchase claims.  
2. **Fuel Purchase Claims**  
   - Households or distributors submit claims indicating the date, type of fuel, and amount spent.  
   - A baseline reference (charcoal costs) is stored for each household or region.  
3. **Oracle Validation**  
   - Oracles verify payment details and cross-check market prices in USD.  
   - The system calculates savings = (baseline expenditure – current expenditure).  
4. **Credential Issuance**  
   - Validated savings amounts are sealed in a verifiable credential, aggregating annual savings.

#### Developer Notes
- Implement a “FuelExpenditureProtocol” that defines the claim schema: [date, paymentIdentifier, fuelCostUSD, baselineFuelType, baselineCostUSD].  
- Oracles can access external market price feeds for currency exchange rates if needed.

### SDG 2: Zero Hunger

**Indicator**: Percentage of households achieving improved diet diversity.  
**Parameter**: Dietary diversity scores.  
**Method**: Ex-Post biannual program surveys.

#### Data Flow
1. **Biannual Surveys**  
   - A standardized form collects dietary diversity information (e.g., number of different food groups consumed).  
2. **Claim Submission**  
   - Field enumerators or household members submit these scores as claims referencing the Household DID.  
   - Surveys may be offline first, then synced when connectivity is available.  
3. **Oracle Verification**  
   - Oracles check for data consistency (e.g., ensuring no duplicates, plausibility checks).  
4. **Aggregation**  
   - The platform calculates the percentage of households above a certain diet diversity threshold.  
   - Final results can be reported at a community or project level in a verifiable credential.

#### Developer Notes
- Store survey forms as JSON (or JSON-LD) referencing question IDs and user responses.  
- Consider a “DietDiversityProtocol” that encodes the standard scoring methodology (e.g., FAO guidelines).

### SDG 3: Good Health and Well-being

**Indicator**: Reduction in respiratory illnesses related to hazardous air pollution (HAP).  
**Parameter**: Self-reported cases of respiratory disease.  
**Method**: Ex-Post biannual household surveys.

#### Data Flow
1. **Household Survey**  
   - Households report incidence of respiratory issues (e.g., cough, shortness of breath).  
2. **Claim Submission**  
   - Survey enumerators upload responses (did the household have X respiratory symptoms?).  
3. **Oracle Cross-Checks**  
   - Verify survey authenticity (signed enumerator’s DID).  
   - Compare responses with known patterns (large outliers or contradictory data might trigger a review).  
4. **Analytics**  
   - Track changes in reported illnesses over time, referencing adoption of cleaner stoves or fuels.

#### Developer Notes
- Align with recognized medical definitions of HAP-related illnesses.  
- Potentially integrate with local clinic data or healthcare partner APIs for validation if available.

### SDG 5: Gender Equality

**Indicators**:
1. Number of hours saved per day on cooking and fuel collection.  
2. Percentage of project employees and agents who are women (target 40%) and reduction in the gender pay gap (<10%).

**Parameter**: Time savings and gender-related employment data.  
**Method**: TBD for time savings; annual audits for employment data.

#### Data Flow (Time Savings)
1. **Time Audit Surveys**  
   - A dedicated protocol collects daily or weekly logs on how many hours are spent cooking or collecting fuel before vs. after intervention.  
2. **Oracle Verification**  
   - Compares self-reported data with other household or device usage claims.  
   - Flags anomalies (e.g., more hours reported saved than total daily cooking time).

#### Data Flow (Employment Metrics)
1. **Organizational DID**  
   - The implementing organization or sub-projects have their own DIDs.  
2. **Employment Audit Claims**  
   - HR or project managers submit annual claims summarizing staff composition, salaries, gender breakdown.  
3. **Third-Party Verification**  
   - Auditors verify payroll records or official employment registers.

#### Developer Notes
- Use dedicated protocols for “TimeSavingsProtocol” and “GenderEmploymentProtocol.”  
- Each protocol can define data validation rules (e.g., maximum hours saved, acceptable pay range).

### SDG 7: Affordable and Clean Energy

**Indicator**: Percentage of households using modern energy cooking devices for >80% of their cooking needs.  
**Parameter**: Household fuel purchase claims.  
**Method**: Ex-Post analysis of fuel purchase claims.

#### Data Flow
1. **Fuel Purchase Claims**  
   - Each household logs purchases of modern cooking fuels (e.g., LPG, biomass pellets) vs. traditional fuels (charcoal, wood).  
2. **Usage Threshold**  
   - The platform calculates the share of modern fuel usage among all cooking fuels for the household.  
3. **Oracle Validation**  
   - Confirms data authenticity (payment receipts, vendor confirmations).  
   - Determines if the household meets the >80% threshold.  
4. **Reporting**  
   - A verifiable credential indicates whether the household is “mostly reliant on modern cooking devices.”

#### Developer Notes
- Potentially incorporate usage sensor data if devices are IoT-enabled.  
- Evaluate partial purchases or splits in multi-fuel scenarios.

### SDG 8: Decent Work and Economic Growth

**Indicator**: Number of young people employed in project-related activities.  
**Parameter**: Number of service delivery claims submitted by youth agents.  
**Method**: Ex-Post analysis of service delivery claims and payment records.

#### Data Flow
1. **Agent DID**  
   - Each youth agent or employee is registered with a DID and includes their age group.  
2. **Service Delivery Claims**  
   - Agents submit claims for tasks performed (e.g., device installations, surveys, training).  
   - Payment records link to these claims.  
3. **Oracle Validation**  
   - Checks that the agent’s credentials confirm they are under a specified age threshold (e.g., 30 years old).  
4. **Aggregation**  
   - The total number of valid claims indicates the level of youth participation.

#### Developer Notes
- Maintain an “AgentProfileProtocol” capturing birthdate or proof-of-age.  
- Combine multiple claims to produce an annual or semi-annual statistic.

### SDG 9: Industry, Innovation, and Infrastructure

**Indicator**: Number of new businesses created in the clean cooking sector.  
**Parameter**: Business registration data and industry reports.  
**Method**: Ex-Post annual industry analysis reports.

#### Data Flow
1. **Business DID Registration**  
   - Newly established businesses get a DID, often referencing official government business IDs or relevant documentation.  
2. **Annual Industry Analysis**  
   - A third-party or project-level Oracle collects official registration data, industry association records, and cross-checks with local registries.  
3. **Claims Submission**  
   - Each new business recognized in the sector is recorded as a claim (e.g., “BusinessA registered on 2025-07-01 under the clean cooking sector code”).  
4. **Credential Issuance**  
   - A verifiable “NewBusinessCredential” indicates the existence and date of incorporation.

#### Developer Notes
- Interfacing with government or chamber of commerce APIs can automate data gathering.  
- Ensure consistent classification of “clean cooking sector” or relevant NAICS/ISIC codes.

### SDG 11: Sustainable Cities and Communities

**Indicator**: Improvement in urban air quality.  
**Parameter**: Air quality data pre- and post-intervention.  
**Method**: Ex-Post third-party air quality monitoring reports.

#### Data Flow
1. **Baseline Air Quality Reports**  
   - Historical city or district-level data is stored as a baseline.  
2. **Periodic Monitoring**  
   - A recognized third-party performs periodic sampling or uses existing city air quality sensors.  
3. **Oracle Integration**  
   - The Oracle checks these official reports, extracting relevant pollutants data (e.g., PM2.5, PM10).  
4. **Claim and Credential**  
   - A claim states changes in pollutant levels compared to the baseline.  
   - Once validated, it’s turned into an “AirQualityCredential.”

#### Developer Notes
- Storing large sensor data sets off-chain; record essential references (hashes) on-chain.  
- Ensure third-party monitoring organizations have recognized credentials or an established DID for trust.

### SDG 13: Climate Action

**Indicator**: Reduction in greenhouse gas emissions from household cooking.  
**Parameter**: Emission reduction claims based on fuel purchase and device usage.  
**Method**: Ex-Post certified units of ITMOs.

#### Data Flow
1. **Fuel Usage & Device Telemetry**  
   - Stoves or households submit usage claims.  
   - Baseline data sets the emission factors for traditional fuels.  
2. **Oracle Validation**  
   - Checks calculations of emission reductions (CO2e) using standardized formulas or project methodologies.  
   - Confirms devices are installed and operational.  
3. **ITMO Credential**  
   - Once validated, the system mints or recognizes ITMOs representing actual emissions avoided.  
4. **On-Chain Audit Trail**  
   - All usage data and ITMO claims are anchored, ensuring no tampering and facilitating cross-border verification.

#### Developer Notes
- Integrate official emission factors and standardized calculation tools.  
- Link the “ITMO credentials” to the relevant national or international registry if needed.

### SDG 15: Life on Land

**Indicator**: Fraction of Non-Renewable Biomass (fNRB) used as cooking fuels.  
**Parameter**: GIS-based surveys modeling spatio-temporal impacts of woodfuel harvesting (MoFuSS).  
**Method**: Ex-Post periodic changes in fNRB values using MoFuSS.

#### Data Flow
1. **GIS Mapping**  
   - Satellite imagery or field data used to model forest regeneration vs. extraction rates.  
2. **MoFuSS Integration**  
   - The Emerging Platform ingests MoFuSS outputs via an Oracle or direct API.  
   - Fraction of Non-Renewable Biomass is updated periodically (e.g., once or twice a year).  
3. **Claim Creation**  
   - A claim states “fNRB for region X in year Y is Z%.”  
4. **Emission Factor Impact**  
   - The platform then applies updated fNRB factors to household-level woodfuel usage claims, refining emission calculations and ecological impact metrics.

#### Developer Notes
- MoFuSS data can be stored off-chain; a cryptographic hash is published on-chain.  
- Recompute the fraction for each region as new GIS data arrives.

### SDG 17: Partnerships for the Goals

**Indicator**: Number of partnerships formed for mitigation activity implementation.  
**Parameter**: Partnership agreements and collaboration reports.  
**Method**: Ex-Ante/Ex-Post partnership evaluations.

#### Data Flow
1. **Partnership DID**  
   - Each partnership (e.g., NGO, private firm) is recorded with a DID.  
2. **Partnership Agreement Claims**  
   - Project administrators submit a claim referencing the agreement date, signatories, and scope of collaboration.  
3. **Oracle Verification**  
   - Validates any official documents or MOU references.  
   - Confirms ongoing partnership status (renewal, project milestones).  
4. **Credential Issuance**  
   - Partnerships are tracked in a “PartnershipCredential,” stating how many new collaborations started or ended in a given timeframe.

#### Developer Notes
- Cross-check local or international project records (e.g., memoranda of understanding).  
- Tag each partnership with relevant SDG targets (not just SDG 17 but also co-benefits).

## 3. General Developer Workflow

1. **Set Up Protocols**  
   - Define protocols for each SDG indicator, clarifying data fields, monitoring intervals, and validation rules.

2. **Data Submission**  
   - Develop or integrate user-facing apps, IoT device pipelines, or partner dashboards that submit claims (fuel purchases, surveys, air quality data, etc.).

3. **Oracle Configuration**  
   - For each indicator, configure oracles to perform validations (e.g., verifying receipts, analyzing survey data, checking satellite imagery).

4. **Credential Issuance**  
   - Once claims pass validation, the platform issues verifiable credentials referencing the relevant SDG indicators.

5. **Reporting & Analytics**  
   - Aggregated credentials can be compiled into project-level or national-level MRV reports.  
   - Tools such as dashboards or external BI systems can query the Emerging Platform’s ledger to generate SDG compliance metrics.

## Security and Data Integrity

- **Cryptographic Signatures**  
  Each claim submission includes a signature from the relevant DID (e.g., enumerator, device, organization), ensuring authenticity and non-repudiation.

- **Immutable Ledger**  
  Key data (references, hashes) are stored on-chain to prevent unauthorized alteration. Large data sets (e.g., scanned forms, satellite images) may reside off-chain, but their hashes are anchored on-chain.

- **Access Control**  
  Role-based permissions ensure only authorized users or oracles can update or verify claims. Household privacy is protected by limiting personally identifiable information in public records.

## Conclusion

By tailoring the Emerging Platform’s flexible dMRV architecture to each SDG indicator, developers can capture, verify, and report credible results across multiple impact domains. Whether it’s financial savings for SDG 1, improved air quality for SDG 11, or new businesses for SDG 9, the platform supports robust data collection methods, secure validation via oracles, and transparent audit trails anchored on a decentralized ledger.

Developers should create specialized protocols for each SDG metric, ensuring consistent data schemas and validation workflows. By combining offline-friendly survey tools, IoT device integration, and periodic third-party audits, the Emerging Platform can streamline ex-post and ex-ante monitoring, build trust with external stakeholders, and deliver accurate, tamper-proof records of progress toward the Sustainable Development Goals.
