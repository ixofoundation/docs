---
stoplight-id: 5glmyf1zolslj
---

# Claims and Collections Queries

The following GraphQL queries enable interaction with claims and claim collections within the IXO ecosystem. These queries help manage submissions, evaluations, and associated metadata.

## Queries

### 1. **ClaimCollections**
Retrieve a list of claim collections filtered by specific conditions.

```graphql
query ClaimCollections {
  claimCollections(
    condition: {entity: "did:ixo:entity:8fcfa96ba4a94e5e9a86407dbf0f682f"}
    orderBy: ID_ASC
  ) {
    totalCount
    edges {
      node {
        id
        admin
        entity
        protocol
        state
        claimSchemaTypesLoaded
        claimsByCollectionId {
          totalCount
        }
        invalidated
        startDate
        endDate
        quota
        count
        evaluated
        approved
        rejected
        disputed
        payments
      }
    }
  }
}
```

### 2. **SingleClaimCollection**
Retrieve detailed information about a single claim collection by its ID.

```graphql
query SingleClaimCollection {
  claimCollection(id: "54") {
    id
    admin
    claimSchemaTypesLoaded
    state
    startDate
    endDate
    entity
    protocol
    quota
    count
    evaluated
    approved
    rejected
    disputed
    invalidated
    payments
    claimsByCollectionId {
      totalCount
      nodes {
        agentAddress
        agentDid
        claimId
        collectionId
        paymentsStatus
        schemaType
        submissionDate
      }
    }
  }
}
```

### 3. **Claims**
Retrieve a list of claims filtered by submission date, collection ID, or evaluation criteria.

```graphql
query Claims {
  claims(
    filter: {
      submissionDate: {greaterThan: "2024-10-28T00:00:00.000"},
      collectionId: {in: ["36"]}
    }
  ) {
    totalCount
    nodes {
      claimId
      collectionId
      schemaType
      submissionDate
      agentDid
      agentAddress
      paymentsStatus
      evaluationByClaimId {
        claimId
        collectionId
        agentDid
        agentAddress
        oracle
        evaluationDate
        status
        reason
        amount
        verificationProof
      }
    }
  }
}
```

### 4. **claimsProcessedToDate**
Retrieve the total count of claims processed to date within specific collections.

```graphql
query claimsProcessedToDate {
  claimCollections(
    filter: {claimsByCollectionIdExist: true, entity: {equalTo: "did:ixo:entity:ffa3180c8e5f313ec74afa4ade32fd60"}}
  ) {
    totalCount
    edges {
      node {
        id
      }
    }
  }
}
```

### 5. **BidsForClaimCollection**
Retrieve entities linked to specific claim collections based on criteria.

```graphql
query BidsForClaimCollection {
  entities(
    filter: {iidById: {linkedEntity: {contains: [{id: "38"}, {type: "ClaimCollection"}, {service: "ixo"}, {relationship: "submission"}]}}}
  ) {
    totalCount
    edges {
      node {
        id
      }
    }
  }
}
```

---

These queries provide the tools to manage, retrieve, and analyze claims and collections within the IXO ecosystem efficiently. By leveraging these, developers can build robust applications that support claim submissions, evaluations, and monitoring.

