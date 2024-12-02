---
stoplight-id: 044xgo10quael
---

# Overview

The **gRPC Gateway API Reference** document serves as a comprehensive guide for developers and integrators working with the IXO blockchain. Its primary purpose is to facilitate efficient interactions with blockchain data by providing a RESTful interface to access gRPC services. The document bridges the gap between gRPC—a protocol commonly used for high-performance applications—and REST, which is more widely compatible and accessible for web development.

This reference guide is essential for those who wish to leverage the IXO blockchain's state queries and other features using familiar RESTful methods, allowing for greater ease of integration and usability in various web and mobile applications.

## Purpose of the Document

The core purpose of this document is to provide a clear, structured, and approachable way for developers to interact with the IXO blockchain through HTTP endpoints. The **gRPC Gateway API Reference** enables the use of REST to execute state queries and access blockchain information without having to fully implement gRPC clients. This allows a broader range of developers, particularly those who are more comfortable with REST APIs, to seamlessly interact with IXO blockchain data.

## What the Document Covers

The document covers a detailed outline of the available API endpoints, along with explanations on how to use them effectively. Specifically, it provides:

- **Endpoint Descriptions**: Each endpoint is clearly documented, including the available HTTP methods, query parameters, and expected responses.
- **Use Cases**: Example scenarios are provided to show how different parts of the blockchain can be queried, making it easy to understand real-world applications.
- **Data Structures**: The data structures returned by the endpoints are explained to help developers understand how to parse and utilise the information received.
- **Error Handling**: Details about common error responses are included to assist developers in debugging and handling exceptions.

## How the gRPC Gateway Works

The **gRPC Gateway** acts as a bridge between gRPC and REST, translating HTTP REST requests into gRPC calls and vice versa. Here’s how it works in the context of the IXO blockchain:

1. **Client Request**: A developer makes a RESTful HTTP request to a specified API endpoint.
2. **Gateway Translation**: The gRPC Gateway receives this HTTP request and converts it into a gRPC request, which is then sent to the appropriate gRPC server.
3. **Response Handling**: The gRPC server processes the request and returns a response, which is translated back into an HTTP response by the Gateway.
4. **Client Response**: The developer receives the REST-style response, which contains the requested blockchain data in a structured JSON format.

This architecture simplifies the development process by allowing applications to work with the IXO blockchain without implementing gRPC-specific libraries or handling protocol buffers directly.

## Key Features

- **REST Access to gRPC**: The ability to interact with gRPC services through REST endpoints, making blockchain integration more accessible for web developers.
- **Simplified Onboarding**: By offering an approachable REST API, developers can easily get started with interacting with the blockchain without the complexities of gRPC.
- **Extensive Endpoint Coverage**: The document provides comprehensive information on IXO-specific endpoints, including details on bonds, claims, entities, epochs, tokens, and more.

## IXO-Specific Endpoints

The **gRPC Gateway API Reference** includes numerous IXO-specific endpoints that are designed to provide access to the blockchain’s specialized features, such as managing claims, bonds, entities, tokens, and other core IXO functionalities. These endpoints ensure that developers can interact with the blockchain in a flexible and powerful way, depending on their use cases.

### Examples of IXO Endpoints

- `/ixo/bonds/{bond_did}`: Retrieve information about a specific bond.
- `/ixo/claims/claims`: Access claims data that has been submitted to the blockchain.
- `/ixo/entity/{id}`: Get details about a specific entity within the IXO network.

These endpoints and many more allow applications to read blockchain state, interact with entities, manage claims, and participate in the IXO ecosystem, all through straightforward REST calls.
