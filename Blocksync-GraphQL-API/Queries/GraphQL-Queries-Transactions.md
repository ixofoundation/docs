---
stoplight-id: 0vjbyj8bx7bhe
---

# Transactions

The IXO Blocksync GraphQL API allows developers to retrieve transaction details with ease and flexibility. These queries enable access to individual transaction data as well as aggregated data within the IXO ecosystem.

## Queries

### **Chain Transactions**
Retrieve a list of transactions with detailed filtering capabilities based on time, sender, receiver, and message type.

```graphql
query ChainTransactions {
  transactions(
    filter: {
      messagesByTransactionHash: {
        some: {
          from: {equalTo: "ixo1wc43xczdzlc623e9ssxkndpqnvgk2vq4hheyq2"}
        }
      }
    },
    orderBy: TIME_ASC
  ) {
    totalCount
    edges {
      node {
        time
        messagesByTransactionHash {
          totalCount
          edges {
            node {
              to
              typeUrl
              transactionHash
              denoms
              tokenNames
              from
              id
            }
          }
        }
      }
    }  
  }
}
```

### **Single Chain Transaction**
Retrieve details of a single transaction using its unique transaction hash.

```graphql
query SingleChainTransaction {
  transaction(
    hash: "F7A3C80F3D97B818D8BC4A88D0D87169C3D2DD23752D8FCCB47F6278080C91D0"
  ) {
    hash
    height
    time
    memo
    fee
    gasUsed
    gasWanted
    code
    messagesByTransactionHash {
      totalCount
      nodes {
        transactionHash
        typeUrl
        denoms
        from
        to
        tokenNames
        value
      }
    }
  }
}
```

---

These queries are essential for accessing and analyzing transaction data, facilitating transparency, and enabling developers to build comprehensive tools around the IXO ecosystem.

