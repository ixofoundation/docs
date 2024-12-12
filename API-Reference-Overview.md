---
stoplight-id: fiyi6i7jtqf6i
tags: [Introduction]
---

# API Reference

The IXO Spatial Web API is comprehensive and spans multiple domains, providing various functions to interact with different components of the IXO ecosystem. The key systems involved in offering these functionalities include:

- [**IXO Protocol Blockchain RPC API**](RPC-API/RPC-API-Overview.md): Manages on-chain data and transactions via direct RPC communication.
- [**IXO Protocol Blockchain gRPC Gateway API**](gRPC-Gateway/gRPC-Gateway-Overview.md): Provides a gRPC REST interface for direct blockchain queries.
- [**IXO Blocksync GraphQL API**](Blocksync-GraphQL-API/Blocksync-GraphQL-API-Overview.md): Provides a GraphQL interface for efficient and flexible querying of indexed blockchain data.
- [**IXO Matrix State Bot API**](Matrix-REST-API/Matrix-REST-API-Overview.md): An interface to the private and secure data vaults stored in Matrix.
- [**AI Companion REST API**](AI-Companion-REST-API/AI-Companion-REST-API-Overview.md): Offers artificial intelligence features and services to enhance the user experience.

Each system contributes a specific part of the overall API, allowing users to leverage their functionalities to build and interact with impactful applications.

The IXO Spatial Web API is organized around REST principles. It uses predictable resource-oriented URLs, accepts form-encoded request bodies, returns JSON-encoded responses, and adheres to standard HTTP response codes, authentication mechanisms, and verbs.

The IXO Blocksync GraphQL API offers a flexible query language, enabling developers to retrieve exactly the data they need from the blockchain. It supports powerful features such as nested queries, filtering, and pagination, making it an ideal choice for efficient data retrieval. The GraphQL API endpoints allow for comprehensive data access, giving users a streamlined experience for querying blockchain information.

<!-- theme: info --> 
> ### Test Mode
>
> You can also use the IXO Spatial Web API in test mode by directing server endpoints to our testnet blockchain.  
> Transactions on the testnet do not involve real tokens or data, and they are not guaranteed to be available in the future.  
> It is advisable to use anonymous or mock data during testing to ensure data privacy and integrity.
