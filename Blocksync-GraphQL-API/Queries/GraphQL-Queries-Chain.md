---
stoplight-id: y3g72ofux901t
---

# Chain State

The IXO Blocksync GraphQL API offers robust capabilities to query blockchain chain-related data. These queries allow developers to retrieve detailed chain-level information, including state and metadata.

## Queries

### **Chain State Overview**

Retrieve the overall state of the blockchain.

```graphql
query ChainState {
  chains {
    totalCount
    nodes {
      chainId
      blockHeight
    }
  }
}
```

This query provides critical details about the blockchain's current state, including the block height and chain ID.

---

These queries provide essential insights into the IXO blockchain's structure and state, enabling developers to monitor, analyze, and interact effectively with the blockchain.

