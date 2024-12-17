---
stoplight-id: 87dvp3tdg18ap
---

# Bonds

The following GraphQL queries enable interaction with the bond management system in the IXO ecosystem. These queries allow developers to retrieve bond-related data, such as details about bonds, associated transactions, and performance metrics.

## Queries

### 1. **Bonds**
Retrieve a list of all bonds with associated metadata and transactional details.

```graphql
query Bonds {
  bonds {
    totalCount
    edges {
      node {
        name
        token
        state
        description
        bondDid
        oracleDid
        creatorDid
        controllerDid
        alphaBond
        functionType
        functionParameters
        txFeePercentage
        exitFeePercentage
        feeAddress
        reserveWithdrawalAddress
        maxSupply
        orderQuantityLimits
        sanityRate
        sanityMarginPercentage
        currentSupply
        reserveTokens
        currentReserve
        availableReserve
        currentOutcomePaymentReserve
        allowSells
        allowReserveWithdrawals
        batchBlocks
        outcomePayment
        bondBuysByBondDid {
          edges {
            node {
              id
            }
          }
        }
        bondSwapsByBondDid {
          edges {
            node {
              id
            }
          }
        }
        reserveWithdrawalsByBondDid {
          edges {
            node {
              id
            }
          }
        }
        shareWithdrawalsByBondDid {
          edges {
            node {
              id
            }
          }
        }
        outcomePaymentsByBondDid {
          edges {
            node {
              id
            }
          }
        }
        bondAlphasByBondDid {
          edges {
            node {
              id
            }
          }
        }
      }
    }
  }
}
```

---

These queries enable developers to retrieve comprehensive data about bonds and their associated financial and operational details, facilitating the creation of robust applications for managing bonds within the IXO ecosystem.

