---
stoplight-id: u3cub67gj0lbn
---

# Claims Verification

This guide will walk you through the process of implementing Claims Verification using IXO protocols and Oracle services that leverage Causal AI models for evaluating claims.

## Overview

The [IXO platform](https://www.ixo.world) enables the creation and verification of Verifiable Claims, which are fundamental to the Internet of Impact. Claims Verification is a crucial step in ensuring the integrity and reliability of impact data. By integrating Causal AI models into Oracle services, we can enhance the evaluation process, providing more accurate and insightful verifications.

### Prerequisites

- Familiarity with IXO platform and protocols
- Access to IXO developer tools and SDK
- Understanding of Causal AI concepts

## Implementing Claims Verification

### Step 1: Set Up the Claim Structure

First, define the structure of your Verifiable Claim using JSON-LD:

```json
{
  "@context": "https://www.w3.org/2018/credentials/v1",
  "id": "http://example.com/claims/1234",
  "type": ["VerifiableCredential", "ImpactClaim"],
  "issuer": "did:ixo:123456789abcdefghi",
  "issuanceDate": "2024-04-12T12:00:00Z",
  "credentialSubject": {
    "id": "did:ixo:subject987654321",
    "impactType": "EmissionReduction",
    "value": 128,
    "unit": "kgCO2"
  }
}
```

### Step 2: Submit the Claim

Reference the IXO Spatial Web implementation guide to [submit claims](../../Implementation-Guides/Claims-Module.md).

### Step 3: Configure the Oracle Service

Set up an Oracle service that incorporates Causal AI models for claim evaluation. This service should be registered with the IXO network:

```javascript
const oracleConfig = {
  name: "CausalAIOracle",
  did: "did:ixo:oracle123456789",
  evaluationModel: "causal-impact-model-v1",
  endpoints: {
    evaluate: "https://api.causal-oracle.example.com/evaluate"
  }
};

ixo.oracles.register(oracleConfig);
```

### Step 4: Implement Causal AI Evaluation

Within your Oracle service, implement the Causal AI model for claim evaluation. This could involve:

1. Data preprocessing
2. Causal graph construction
3. Counterfactual analysis
4. Impact estimation

Here's a simplified example of how the evaluation logic might look:

```python
import causal_impact

def evaluate_claim(claim_data):
    # Preprocess claim data
    time_series = preprocess_data(claim_data)
    
    # Perform causal impact analysis
    impact = causal_impact.analyze(time_series, intervention_point)
    
    # Evaluate the claim based on the causal impact results
    if impact.is_significant() and impact.relative_effect > 0.1:
        return {
            "status": "VERIFIED",
            "confidence": impact.confidence,
            "estimatedImpact": impact.estimated_effect
        }
    else:
        return {
            "status": "REJECTED",
            "reason": "Insufficient causal impact"
        }
```

### Step 5: Process Verification Results

Once the Oracle service has evaluated the claim, process the results and update the claim status on the IXO network:

```javascript
const processVerification = async (claimId, verificationResult) => {
  try {
    await ixo.claims.updateStatus(claimId, verificationResult);
    console.log('Claim verification processed:', claimId);
  } catch (error) {
    console.error('Error processing verification:', error);
  }
};
```

### Step 6: Using IXO Spatial Web ClientSDK Methods

The IXO Spatial Web ClientSDK offers several methods that can be used to facilitate claims verification and management. Some relevant methods include:

- **GrantEntityAccountClaimsEvaluateAuthzThroughAuthz**: Grants claim evaluation authorization through existing authorizations.
- **MsgExecAgentEvaluate**: Executes an evaluation of a claim, determining its approval status.
- **DisputeClaim**: Initiates a dispute for a specific claim.
- **MsgExecWithdrawal**: Executes a withdrawal of a payment related to a claim.


## Best Practices

1. Ensure your Causal AI models are well-calibrated and regularly updated with new data.
2. Implement robust error handling and logging in your Oracle service.
3. Use standardized claim schemas to ensure interoperability across different projects and domains.
4. Regularly audit and validate the performance of your verification system.

## Conclusion

By implementing Claims Verification using IXO protocols and Causal AI Oracle services, you can create a robust system for evaluating impact claims. This approach combines the benefits of blockchain-based verifiable claims with the analytical power of causal inference, leading to more accurate and trustworthy impact assessments in the Internet of Impact ecosystem.


