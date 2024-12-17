---
stoplight-id: pggn608pk7vps
---

# ixoSwap

The following GraphQL queries enable interaction with the ixoSwap system within the IXO ecosystem. These queries support retrieving swap histories and analyzing token swap data.

## Queries

### 1. **SwapHistories**
Retrieve a list of token swap price histories ordered by timestamp.

```graphql
query SwapHistories {
  ixoSwapPriceHistories(
    orderBy: TIMESTAMP_DESC
  ) {
    totalCount
    edges {
      node {
        address
        id
        nodeId
        timestamp
        token2Price
        token2Volume
        token1155Price
        token1155Volume
      }
    }
  }
}
```

---

These queries provide access to critical ixoSwap data, enabling developers to build applications that leverage token swap analytics and historical data.

