---
stoplight-id: 75nnbyrg3k6yk
---

# ClaimEvaluations

This guide outlines the process for implementing Claims Verification using IXO protocols and Oracle services, leveraging Causal AI models for accurate and insightful claim evaluations.

## Overview

Claims Verification ensures the integrity and reliability of submitted data by validating Verifiable Claims against predefined criteria. By integrating Causal AI models within Oracle services, this process enables nuanced evaluations, incorporating counterfactual reasoning and causal impact analysis to enhance the verification process.

Prerequisites
- Understanding of Verifiable Claims and JSON-LD standards
- Familiarity with IXO developer tools, SDKs, and protocols
- Access to oracles configured with Causal AI models

## Implementation

### Step 1: Define the Claim Structure

Start by defining the structure of the Verifiable Claim using the JSON-LD format. This ensures compatibility with IXO protocols and linked-data frameworks:
```
{
  "@context": "https://www.w3.org/2018/credentials/v1",
  "id": "http://example.com/claims/1234",
  "type": ["VerifiableCredential", "ImpactClaim"],
  "issuer": "did:ixo:issuer123",
  "issuanceDate": "2025-01-01T00:00:00Z",
  "credentialSubject": {
    "id": "did:ixo:subject456",
    "impactType": "EmissionReduction",
    "value": 150,
    "unit": "kgCO2"
  }
}
```
### Step 2: Submit the Claim

Submit the structured claim to the IXO Claims Module using the platform’s SDK or API. Follow the relevant implementation guide for submission specifics.

### Step 3: Set Up an Oracle Service

Configure an Oracle service to evaluate claims using Causal AI. The Oracle should be registered on the IXO network with the appropriate evaluation endpoints:
```
const oracleConfig = {
  name: "CausalImpactOracle",
  did: "did:ixo:oracle789",
  evaluationModel: "causal-model-v2",
  endpoints: {
    evaluate: "https://api.oracle.example.com/evaluate"
  }
};

ixo.oracles.register(oracleConfig);
```
### Step 4: Implement the Evaluation Logic

The Oracle service should include a Causal AI model for analyzing the claim. Key steps involve preprocessing data, constructing causal models, and performing impact analysis.

Example:

from causal_impact import CausalImpact

def evaluate_claim(data):
```
    # Preprocess the data for causal analysis
    time_series_data = preprocess_claim_data(data)
    
    # Define intervention point
    intervention_point = data['intervention_point']
    
    # Perform causal analysis
    impact = CausalImpact(time_series_data, intervention_point)
    
    # Check if the impact is significant
    if impact.is_significant() and impact.effect > threshold:
        return {
            "status": "VERIFIED",
            "confidence": impact.confidence_level,
            "impactValue": impact.effect
        }
    else:
        return {
            "status": "REJECTED",
            "reason": "Insufficient impact evidence"
        }
```
### Step 5: Process Verification Results

Process the results of the claim evaluation and update its status on the IXO network:
```
const updateClaimStatus = async (claimId, result) => {
  try {
    await ixo.claims.updateStatus(claimId, result);
    console.log('Claim verification updated successfully:', claimId);
  } catch (err) {
    console.error('Error updating claim status:', err);
  }
};
```
### Step 6: Utilize SDK Methods

Leverage IXO’s ClientSDK to facilitate operations related to claims evaluation and management, such as:
- AuthorizeEvaluation: Grant permissions for evaluating claims.
- ExecuteEvaluation: Trigger evaluations and update claim statuses.
- DisputeClaim: Challenge the results of an evaluation if necessary.

## Best Practices
	1.	Maintain Data Quality: Ensure input data for claims and Causal AI models is accurate and complete.
	2.	Monitor Model Performance: Regularly evaluate and update Causal AI models to adapt to changing conditions or new data.
	3.	Standardize Claims: Use common schemas and ontologies to enhance interoperability.
	4.	Log and Audit: Implement robust logging and auditing mechanisms for traceability and accountability.
  

## Conclusion

Integrating Claims Verification with Causal AI Oracle services enables reliable and data-driven evaluation processes. This approach enhances the credibility of claims by combining cryptographic verifiability with advanced causal reasoning, offering a scalable solution for automated and transparent claim validation.
