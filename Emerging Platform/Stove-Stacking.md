---
stoplight-id: 457c5odfq1xnp
---

# Stove-Stacking

## Definition and Challenges

Stove stacking occurs when a household or entity uses multiple cooking devices (or multiple fuels) for different needs. For instance, a household may use both an LPG cookstove and a traditional wood stove. This introduces several MRV challenges:

- Overlapping Emissions: It can be difficult to isolate the exact contribution of each device when multiple devices operate in parallel.  
- Potential Overcounting: If all devices are assumed to replace the same baseline emissions, the reported overall mitigation can be inflated.  
- Complex Usage Patterns: Households may vary usage based on factors like cooking time, type of meal, or season.

## Data Model for Stove Stacking

### Household as the Core Entity
The platform groups devices under a single Household DID, providing a unified identity for all cooking activities. This approach:
- Links each device (e.g., biomass stove, LPG stove) to the same household.  
- Aggregates device-specific claims into a single data repository.  
- Facilitates correlation of multi-device usage by referencing device-level data under a single household context.

### Device Metadata and Claims
Each device generates usage (e.g., burn time, fuel consumption) and event data (e.g., repairs, deliveries), which are captured as claims:
- Claims are cryptographically signed at the device level, ensuring authenticity.  
- These claims link back to the household entity, allowing the platform to see if multiple devices are in use at the same time or within the same reporting period.  
- Cross-device analysis is then possible, since all claims share the same household reference.

## Detecting Stove Stacking

### Measurement
- IoT Telemetry or Mobile App Logging: Each device periodically transmits usage data. For instance, an electric pressure cooker might send daily kWh readings, while a biomass stove might log weekly fuel deliveries.  
- Data Validation: The platform automatically checks incoming data for timestamp continuity and authenticity (via digital signatures).

### Reporting
- Household-Level Aggregation: The platform aggregates all usage and delivery claims for the same household.  
- Unified Report Generation: Emissions are calculated for each device-fuel combination. For example, Device A (electric) might show X kWh consumed, while Device B (biomass) shows Y kg of pellets burned.

### Verification
- Oracle Analysis: Oracles or approved verifiers validate usage claims against the household profile. They confirm that overlapping device usage is not double-counting the same baseline emissions.  
- Anomaly Detection: If the system detects that usage data for multiple stoves is higher than plausible cooking requirements for a single household, it flags the data for deeper review or adjustments.

## Counterfactual Causal Analysis

### Purpose of Counterfactuals
Counterfactual causal analysis attempts to answer: “What would have happened if a particular device (or combination of devices) had not been used?” In other words, how do we differentiate the emission reductions from the new, cleaner stoves from the baseline scenario in which a more polluting device might have been used?

### Constructing the Baseline Scenario
- Historical Data: The household’s historical usage of traditional stoves (like wood or charcoal) is used to estimate typical cooking energy needs, cooking durations, and emissions.  
- Comparable Households: Where historical data is unavailable, the platform can use data from comparable households in the same region or with similar demographics.  
- Exogenous Factors: Factors like seasonal variations or family size changes are also integrated into the baseline model.

### Causal Model
The platform’s AI or Oracles use a causal graph linking each device’s usage to emission outcomes:
1. **Nodes**: Households, devices, usage metrics (e.g., burn time, fuel consumption), emission levels, and external factors (e.g., number of meals, household size).  
2. **Edges**: Cause-and-effect relationships (e.g., “the presence of a clean cookstove reduces the total biomass used for cooking”).  
3. **Counterfactual Computations**: By removing or substituting one device from the model, the system can infer the household’s expected emissions had that device not been used.

### Quantifying Emission Reductions
When a household uses multiple stoves, the causal model partitions the contribution of each device:
- **Observed Data**: Actual usage data from all stoves in the household.  
- **Counterfactuals**: Hypothetical usage data if device A was absent (or replaced by a more polluting device).  
- **Marginal Contribution**: The difference between the observed household emissions and the counterfactual scenario (no device A) indicates how much device A alone reduced emissions.

## Implementation Details and Data Flows

### Causal Analysis of Stove-Stacking
```pseudo
function performStoveStackingAnalysis(householdId, devices, period):
    // Step 1: Retrieve the claims for each device
    usageDataAll = []
    for device in devices:
        usageDataDevice = getUsageData(householdId, device, period)
        usageDataAll.append(usageDataDevice)

    // Step 2: Construct causal graph
    causalGraph = buildCausalGraph(usageDataAll, otherRelevantFactors)

    // Step 3: For each device, remove it from the model (counterfactual) and recompute emissions
    results = {}
    baselineEmissions = estimateBaselineEmissions(householdId, period)
    actualEmissions = computeActualEmissions(usageDataAll)

    for device in devices:
        // create a scenario without the device
        usageDataCounterfactual = removeDeviceUsage(device, usageDataAll)
        emissionsWithoutDevice = computeActualEmissions(usageDataCounterfactual)

        deviceEmissionReduction = (emissionsWithoutDevice - actualEmissions)
        results[device.id] = {
            "marginalReduction": deviceEmissionReduction,
            "observedUsage": usageDataDevice
        }

    // Step 4: Summarize results
    return {
        "baselineEmissions": baselineEmissions,
        "actualEmissions": actualEmissions,
        "deviceContributions": results
    }
```

### Integration into dMRV Workflow
1. **Data Ingestion**: Real-time or batch usage logs come in from all stoves.  
2. **Household Aggregation**: Claims are grouped by household.  
3. **Causal Analysis Engine**: Periodically (e.g., monthly), the Oracle triggers the counterfactual analysis using the collected usage data to determine each stove’s unique contribution.  
4. **Verification & Credentialing**: Once the system or an external auditor validates these results, the platform can issue distinct verifiable credentials representing the marginal emission reductions attributable to each stove.

## Preventing Overcounting or Underreporting

### Overcounting Prevention
- Household View: Because every device belongs to the same household entity, it’s impossible for the system to claim multiple baseline offsets for the same cooking needs. The causal analysis enforces exclusive attribution of emission reductions.

### Underreporting Avoidance
- Detailed Telemetry: If a stove is underutilized or offline, usage data naturally drops. However, if the household relies more on another stove in parallel, the system captures the shift in usage patterns.  
- Automated Flags: If usage data for one device drastically declines while usage for another device spikes, the system can confirm whether a switch is valid or if there’s a data anomaly (e.g., sensor failure).

### Advantages of This Approach

1. **Precision**: Real-time, device-level telemetry with cryptographic signatures allows the platform to account for all usage, preventing manual misreporting.  
2. **Scalability**: The graph-based approach and Oracle verification are applicable to large-scale programs with thousands of households and multiple stove types.  
3. **Regulatory Trust**: Detailed, transparent, and counterfactually validated data is more credible to auditors, carbon offset buyers, and national/international registries (e.g., ITMO frameworks).  
4. **Behavior Insights**: Stove-stacking patterns reveal user preferences and cooking habits, helping improve program design or fuel supply logistics.

## Conclusion

By blending robust data aggregation, cryptographic security, and causal AI, the Emerging Platform’s dMRV system can accurately track stove stacking. Counterfactual causal analysis gives a granular view of how each device contributes to emission reductions, isolating the real impact of new, cleaner cookstoves. This rigorous approach ensures that every carbon credit or ITMO claim is rooted in verifiable, precise data—meeting the demands of modern climate finance and policy frameworks.
