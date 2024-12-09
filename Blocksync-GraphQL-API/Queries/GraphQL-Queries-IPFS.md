---
stoplight-id: 2qzm2oq6k43ai
---

# IPFS

The IXO Blocksync GraphQL API enables interaction with the InterPlanetary File System (IPFS) to manage and query distributed data. These queries allow developers to retrieve file metadata and content stored in IPFS.

## Queries

### **Retrieve IPFS Content**

Fetch details of IPFS content, including its CID, type, and raw data.

```graphql
query IPFS {
  ipfs {
    totalCount
    nodes {
      cid
      contentType
      data
    }
  }
}
```

This query provides essential information about the IPFS-stored content:

- **CID (Content Identifier):** A unique identifier for the IPFS file.
- **Content Type:** Describes the type of data stored (e.g., text, JSON, image).
- **Data:** Contains the actual raw data or payload stored in IPFS.

### Use Cases

- **Metadata Management:** Retrieve details of files for analysis or integration with blockchain entities.
- **Data Validation:** Validate stored content using the CID to ensure integrity.
- **Distributed Content Retrieval:** Fetch and utilize data distributed across the IPFS network.

---

These queries provide seamless access to IPFS data, supporting decentralized applications and data-driven functionalities within the IXO ecosystem.

