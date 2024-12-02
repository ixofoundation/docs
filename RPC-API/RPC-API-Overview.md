---
stoplight-id: boai2mlhqjbg4
---

# IXO RPC API Overview

The **IXO RPC API Documentation** provides a comprehensive guide to the protobuf-based APIs, which define key message types and services used throughout the IXO blockchain ecosystem. This document serves as a foundation for developers and integrators to understand the core building blocks—such as messages, events, and enquiries—available within the IXO blockchain infrastructure.

## Purpose of the Document

The core purpose of this document is to provide developers with a clear and structured overview of the IXO blockchain's protocol messages. These messages form the basis for transactions, events, and state enquiries, enabling efficient interactions with the blockchain's various features, such as bonds, claims, entities, epochs, and more. This documentation is essential for building decentralised applications that leverage the core functionalities of the IXO blockchain.

## What the Document Covers

The protocol documentation outlines all available protobuf definitions and their role within the IXO blockchain, including:

- **Messages**: Detailed descriptions of different types of messages, such as those for creating, editing, or querying blockchain data. Each message structure is thoroughly explained to help developers use it effectively.
- **Events**: Descriptions of blockchain events that trigger during significant transactions or state changes, such as bond creation or claim submissions.
- **Enquiries**: Definitions of enquiries that developers can use to request information from the blockchain, including parameters, responses, and potential use cases.
- **Data Structures**: Explanations of the data structures within the protobuf definitions to provide insight into how blockchain data is stored and transferred.

## Key Sections of the Protocol Documentation

The **Protocol Documentation** is divided into several sections, each corresponding to a specific part of the IXO blockchain:

1. **Claims Module**: Defines messages, events, and enquiries for managing claims, disputes, and payment transactions, supporting verifiable impact reporting.

2. **Entities Module**: Provides the necessary definitions for interacting with entities in the IXO ecosystem, such as creating and updating entity records.

3. **IID (Interchain Identifier) Module**: Defines the structure and messages for managing decentralised identifiers and related meta-data.

4. **Epochs, Tokens, and Liquid Stake Modules**: Covers messages and events related to epoch management, token minting and burning, and liquid staking.

5. **Bonds Module**: Provides messages, events, and enquiries related to the creation and management of bonds, including buy, sell, and swap orders.

## How the Protocol Documentation Helps

This documentation acts as a crucial resource for developers building on the IXO blockchain. It provides:

- **Detailed Message Structures**: Each protobuf message is broken down into its individual fields, making it easier to understand how to construct requests or handle responses.
- **Event Tracking**: A list of blockchain events that applications can use to monitor and respond to changes in blockchain state, providing reactive capabilities for decentralised apps.
- **Enquiry and Transaction Support**: Comprehensive definitions of available enquiries and transaction messages, enabling seamless integration with the blockchain and facilitating interactions with on-chain data.

## Examples of Use Cases

The Protocol Documentation is particularly useful for:

- **Entity Management**: Managing decentralised identifiers and linked resources with messages such as `MsgCreateEntity` and `MsgAddLinkedClaim` to support decentralised identity solutions.
- **Submitting and Evaluating Claims**: Using `MsgSubmitClaim` and related messages to create verifiable claims and participate in impact projects, ensuring transparency and accountability.
- **Creating and Managing Bonds**: Using `MsgCreateBond` to set up token bonding curves and `MsgBuy` to facilitate purchases, supporting projects that require dynamic token economics.

## Additional Resources

To further support your understanding and implementation of the IXO Protocol, the following resources are available:

- **IXO Spatial Web Multiclient SDK**: This TypeScript SDK enables seamless interaction with the IXO Blockchain, providing access to RPC messages and more. Comprehensive documentation and examples are available in the [GitHub repository](https://github.com/ixofoundation/ixo-MultiClient-SDK).

- **IXO Blockchain GitHub Repository**: The core codebase of the IXO Blockchain, built using the Cosmos SDK, Tendermint, and IBC, can be found in the [GitHub repository](https://github.com/ixofoundation/ixo-blockchain). This repository contains custom modules for bonds, claims, entities, and more, providing developers with the necessary tools to build decentralised solutions.

