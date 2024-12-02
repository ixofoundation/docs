---
stoplight-id: kzy4fdwcn0pmw
---

# IXO Blocksync GraphQL API Overview

The **IXO Blocksync GraphQL API Documentation** provides a comprehensive guide to the schema definitions used to interact with the IXO blockchain via the Blocksync GraphQL API. This document offers developers an overview of how to query blockchain data, filter information, and interact with IXO's decentralised features in a flexible, user-friendly manner.

## Purpose of the Document

This document introduces developers to the key components of the IXO Blocksync GraphQL API. It helps developers understand how to utilise the schema for querying blockchain data, interacting with decentralised entities, and building applications that rely on GraphQL to seamlessly access blockchain services. The Blocksync GraphQL API offers a powerful way to interact with blockchain features such as bonds, claims, entities, and more.

## What the Document Covers

The Blocksync GraphQL API documentation includes a detailed overview of all major types, queries, and custom scalars available within the IXO blockchain environment via the Blocksync GraphQL API, including:

- **Scalars**: Custom scalar types, such as `BigFloat`, used to represent high-precision values crucial for blockchain operations.
- **Filters**: Input filter definitions like `BigFloatFilter`, which are used to apply logical conditions when querying data.
- **Types and Queries**: Definitions of core types and queries that allow developers to interact with blockchain data, including retrieving and manipulating entities, claims, and other decentralised features.
- **Directives**: Details about GraphQL directives like `@specifiedBy`, which help define the behaviour of custom scalar types within the blockchain schema.

## Key Sections of the Schema Documentation

The **Blocksync GraphQL API Documentation** is divided into several sections to facilitate a deep understanding of its components:

### 1. Scalars and Directives

This section defines custom scalar types such as `BigFloat`, which provide precision beyond typical floating-point values. The `@specifiedBy` directive is used to add metadata to scalars, specifying their behaviour.

### 2. Filters

This section includes input filters like `BigFloatFilter` that allow developers to apply specific conditions when querying blockchain data. Filters are combined using logical operations, making it easy to conduct complex searches.

### 3. Core Types

Defines the various types within the IXO blockchain, such as entities, bonds, and claims. Each type is designed to represent a real-world concept in the decentralised ecosystem.

### 4. Queries

Provides access to key blockchain features via queries. Queries are used to fetch data from the blockchain. Note that there are currently no mutations enabled in this API; only queries are available for interacting with the blockchain.

## How the Schema Documentation Helps

This documentation is an invaluable resource for developers who wish to use GraphQL to interact with the IXO blockchain. It provides:

- **High Precision Data Handling**: Custom scalars like `BigFloat` ensure that data requiring high precision, such as financial calculations, is handled accurately.
- **Flexible Filtering**: Input filters such as `BigFloatFilter` allow developers to apply complex logical conditions when querying blockchain data, making the GraphQL API highly flexible.
- **Seamless Data Interaction**: Queries are designed to provide an intuitive way to access blockchain data, supporting a wide range of use cases from data retrieval to interacting with various on-chain entities.

## Examples of Use Cases

The Blocksync GraphQL API Documentation is particularly useful for:

- **Blockchain Data Queries**: Use predefined queries to access information about bonds, claims, entities, and other decentralised features within the IXO blockchain.
- **High Precision Financial Operations**: Scalars like `BigFloat` are used to handle token economics, ensuring that high precision calculations are supported for financial applications on the blockchain.

## Additional Resources

To further support your understanding and use of the IXO Blocksync GraphQL API, the following resources are available:

- **IXO Blocksync Core and Blocksync GitHub Repositories**: The Blocksync GraphQL API is provided by the [ixo-blocksync-core](https://github.com/ixofoundation/ixo-blocksync-core) and [ixo-blocksync](https://github.com/ixofoundation/ixo-blocksync) GitHub repositories. These repositories include the core components that power the API and provide developers with the necessary tools to build decentralised solutions.

