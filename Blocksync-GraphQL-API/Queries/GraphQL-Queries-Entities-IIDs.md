---
stoplight-id: gg79oo15fhpeq
---

# Entities and IIDs

The following GraphQL queries allow you to interact with and retrieve information about entities and their associated interchain identifiers (IIDs) within the IXO ecosystem. These queries are foundational for managing and analyzing entities.

## Queries

### 1. **EntitiesList**
Retrieve a list of entities based on specific filters and sorting criteria.

```graphql
query EntitiesList {
  entities(
    filter: {id: {
      in: [
        "did:ixo:entity:21392efa0725b5be68d8f8f776606dad",
      ]}
    }
    orderBy: RELAYER_NODE_ASC
  ) {
    totalCount
    edges {
      node {
        id
        type
        entityVerified
        owner
        relayerNode
      }
    }
  }
}
```

### 2. **EntitiesByType**
Retrieve all entities of a specific type.

```graphql
query EntitiesByType {
  entities(filter: {type: {equalTo: "asset"}}) {
    totalCount
    edges {
      node {
        id
        type
        entityVerified
        owner
        relayerNode
        linkedEntity
      }
    }
  }
}
```

### 3. **EntitiesByOwner**
Retrieve entities owned by a specific address.

```graphql
query EntitiesByOwner {
  entities(
    filter: {owner: {equalTo: "ixo1f4ps32n86vvkt9dcnwwf7yaegtv6wcqxwtktag"}}
  ) {
    totalCount
    edges {
      node {
        id
        entityVerified
        status
        type
        owner
        relayerNode
        startDate
        endDate
        context
        service
        settings
        linkedResource
      }
    }
  }
}
```

### 4. **EntitiesByExternalId**
Retrieve entities based on their external IDs.

```graphql
query EntitiesByExternalId {
  entities(
    filter: {externalId: {in: ["202200034", "310022155", "310002493", "310032821", "310034195"]}}
  ) {
    totalCount
    edges {
      node {
        id
        type
        alsoKnownAs
        externalId
        context
      }
    }
  }
  claimCollections(filter: {}) {
    totalCount
  }
}
```

### 5. **EntitiesByRelayerNodeAndType**
Retrieve entities filtered by a specific relayer node and type.

```graphql
query EntitiesByRelayerNodeAndType {
  entities(
    filter: {relayerNode: {equalTo: "did:ixo:entity:a1fcead81eab2f1158a726597d872413"}, 
      type: {equalTo: "protocol"}}
  ) {
    totalCount
    edges {
      node {
        id
        type
        entityVerified
        status
        owner
        startDate
        endDate
        metadata
      }
    }
  }
}
```

### 6. **EntitiesByContextClass**
Retrieve entities based on a specific context class.

```graphql
query EntitiesByContextClass {
  entities(
    filter: {iidById: {context: {contains: [{key: "class", val: "did:ixo:entity:7f0cc7a072d514b38cb90bdf2e215901"}]}}}
  ) {
    totalCount
    edges {
      node {
        id
        alsoKnownAs
        externalId
        owner
      }
    }
  }
}
```

### 7. **EntitiesByAlsoKnownAs**
Retrieve entities based on their `alsoKnownAs` identifiers.

```graphql
query EntitiesByAlsoKnownAs {
  entities(filter: {and: {iidById: {and: {alsoKnownAs: {in: ["{id}#1"]}}}}}) {
    totalCount
    edges {
      node {
        id
        type
        alsoKnownAs
        externalId
        context
        metadata
        settings
      }
    }
  }
}
```

### 8. **SingleEntity**
Retrieve detailed information about a single entity by its ID.

```graphql
query SingleEntity {
  entity(id: "did:ixo:entity:3700e507b54ba7092d3f1c4873af26ab") {
    id
    type
    status
    entityVerified
    startDate
    endDate
    owner
    relayerNode
    controller
    context
    metadata
    alsoKnownAs
    externalId
    service
    settings
    linkedResource
    linkedEntity
    linkedClaim
    accounts
    accordedRight
    assertionMethod
    authentication
    capabilityDelegation
    capabilityInvocation
    credentials
    keyAgreement
    verificationMethod
  }
}
```

### 9. **SingleIID**
Retrieve detailed information about a specific IID by its ID.

```graphql
query SingleIID {
  iids(
    filter: {id: {includes: "did:x:zQ3shZ7Cv2y6wq5mcSun2GDp5WSJz8Vhe4uXRQxqrdz5BRqjR"}}
  ) {
    totalCount
    edges {
      node {
        id
        context
        controller
        verificationMethod
        authentication
        assertionMethod
        keyAgreement
        service
        metadata
        accordedRight
        alsoKnownAs
        capabilityDelegation
        capabilityInvocation
        linkedClaim
        linkedEntity
        linkedResource
      }
    }
  }
}
```

---

These queries form the backbone for interacting with entities and IIDs within the IXO ecosystem, allowing developers to access, filter, and retrieve entity-related data efficiently.

