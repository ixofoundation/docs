---
stoplight-id: ngpxlto2rafnb
---

# Tokens

The following GraphQL queries allow you to retrieve information about tokens and their associated metadata within the IXO ecosystem. These queries support token management, tracking, and analytics.

## Queries

### 1. **AccountTokens**
Retrieve token balances for a specific account. Example of an account is a customer who has purchased an Impact Asset, for example a SupaMoto Nifty.

```graphql
query AccountTokens {
  getTokensTotalForEntities(address: "ixo1abc45d6xyz3egcz3nqlfc2elpq3h6usya1b3cd")
}
```

### 2. **TokenClasses**
Retrieve information about all available token classes.

```graphql
query TokenClasses {
  tokenClasses {
    nodes {
      type
      supply
      stopped
      paused
      nodeId
      name
      minter
      image
      description
      contractAddress
      class
      cap
    }
  }
}
```

### 3. **Carbon Token**
Retrieve details of a specific token by its ID.

```graphql
query CarbonToken {
  entities(filter: {iidById: {context: {contains: [{key: "class", val: "did:ixo:entity:4d94f9b6078432648a755203eed50644"}]}}}) {
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

### 4. **TokensQueries**
Retrieve aggregated token information for a specific account.

```graphql
query TokensQueries {
  getAccountTokens(address: "ixo1abc45d6xyz3egcz3nqlfc2elpq3h6usya1b3cd")
  getTokensTotalByAddress(address: "ixo1abc45d6xyz3egcz3nqlfc2elpq3h6usya1b3cd")
  getTokensTotalForEntities(address: "ixo1abc45d6xyz3egcz3nqlfc2elpq3h6usya1b3cd")
}
```

---

These queries enable developers to efficiently interact with the IXO ecosystem's token-related functionalities, providing detailed and aggregated token data for enhanced application capabilities.

