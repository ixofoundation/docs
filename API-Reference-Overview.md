---
stoplight-id: fiyi6i7jtqf6i
tags: [Introduction]
---

# API Reference

The IXO Spatial Web API is comprehensive and spans multiple domains, providing various functions to interact with different components of the IXO ecosystem. This documentation describes the Create, Read, Update, Delete, and List (CRUDL) functions available across these domains. The key systems involved in offering these functionalities include:

- **IXO Impact Hub Blockchain**: Manages on-chain data and transactions.
- **IXO Blocksync Block Indexer**: Provides easy and efficient querying of blockchain data.
- **IXO Data Matrix**: Stores and organizes off-chain data for detailed analysis and integration.

Each system contributes a specific part of the overall API, allowing users to leverage their functionalities to build and interact with impactful applications.

The IXO Spatial Web API is organized around REST principles. It uses predictable resource-oriented URLs, accepts form-encoded request bodies, returns JSON-encoded responses, and adheres to standard HTTP response codes, authentication mechanisms, and verbs.

You can also use the IXO Spatial Web API in **test mode** by directing server endpoints to our testnet blockchain. Transactions on the testnet do not involve real tokens or data, and they are not guaranteed to be available in the future. It is advisable to use anonymous or mock data during testing to ensure data privacy and integrity.

