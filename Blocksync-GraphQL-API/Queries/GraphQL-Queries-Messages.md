---
stoplight-id: nizmvuti0170f
---

# Messages

The IXO Blocksync GraphQL API provides a powerful way to query and analyze blockchain messages within the IXO ecosystem. The following queries allow developers to retrieve detailed message data to support diverse use cases.

## Queries

### **Messages Overview**
Retrieve blockchain messages with detailed information for each transaction.

```graphql
query Messages {
  messages(
    filter: {
      typeUrl: {includes: "/ixo.entity.v1beta1.MsgCreateEntity"}
    }
    orderBy: TIMESTAMP_DESC
  ) {
    totalCount
    edges {
      node {
        typeUrl
        transactionHash
        from
        to
        timestamp
        value
      }
    }
  }
}
```

This query retrieves all messages filtered by type and ordered by the latest timestamp.

### **Messages by Transaction Hash**
Retrieve messages associated with a specific transaction.

```graphql
query MessagesByTransactionHash {
  transaction(
    hash: "F7A3C80F3D97B818D8BC4A88D0D87169C3D2DD23752D8FCCB47F6278080C91D0"
  ) {
    messagesByTransactionHash {
      totalCount
      edges {
        node {
          typeUrl
          transactionHash
          from
          to
          timestamp
          value
        }
      }
    }
  }
}
```

This query fetches messages tied to a specific transaction identified by its hash.

---

These queries are indispensable for understanding the granular details of transactions, aiding in debugging, and enhancing application functionality built on the IXO ecosystem.

