---
stoplight-id: iib40vkr7oefm
---

# IXO Spatial Web Multiclient SDK

The **IXO Spatial Web Multiclient SDK** is a core tool that enables developers to interact with the IXO blockchain efficiently. This SDK provides access to essential blockchain services, allowing developers to create transactions, manage queries, and interact with smart contracts—all through a unified and simplified interface. This document offers a high-level guide to understanding and using the IXO Spatial Web Multiclient SDK, complementing the extensive documentation available in the GitHub repository.

## Getting Started

The **IXO Spatial Web Multiclient SDK** can be easily installed via npm, providing a streamlined way to integrate blockchain functionality into your application:

```bash
npm i @ixo/impactxclient-sdk
```

- **NPM Package**: [IXO Spatial Web Multiclient SDK](https://www.npmjs.com/package/@ixo/impactxclient-sdk)
- **GitHub Repository**: [IXO Multiclient SDK GitHub](https://github.com/ixofoundation/ixo-multiclient-sdk)

The GitHub repository contains extensive documentation that goes into detail about each feature and how it can be used. Below, we provide an overview of the key capabilities and high-level guidance on how to get started.

## Purpose of the SDK

The **IXO Spatial Web Multiclient SDK** is designed to simplify interactions with the IXO blockchain. It abstracts complex blockchain operations and presents developers with a user-friendly interface for creating transactions, handling queries, and managing various blockchain services. This makes it easier for developers to build decentralised applications (dApps) that leverage the IXO blockchain for social, environmental, and economic impact.

## Key Features

### 1. Blockchain Interaction

The SDK allows developers to interact directly with the IXO blockchain for both testnet and mainnet environments. This feature is vital for:

- **Transaction Management**: Developers can create, sign, and submit transactions easily.
- **State Queries**: The SDK supports blockchain state queries, enabling developers to fetch information like account balances, entity statuses, and more.
- **Smart Contracts Integration**: Interacting with CosmWasm smart contracts becomes more accessible through the provided APIs, allowing developers to execute, instantiate, and query smart contracts.

### 2. Modular Design

The SDK is modular in nature, meaning developers can pick and choose the components they need for their specific use case. This makes the SDK adaptable and useful for a range of implementations, from small applications to large-scale dApps.

### 3. Developer-Friendly Testing

Tests for the SDK are available in the GitHub repository within the `__tests__` directory. These tests can be uncommented and run to help developers better understand how different functionalities of the SDK work.

- **Test Directory**: [View Tests](https://github.com/ixofoundation/ixo-multiclient-sdk/tree/84f31673e9ea2ada7f31175bc665a54d238e1601/__tests__)
- **Testing Guidelines**: Most tests are commented out by default to prevent accidental execution. Developers are encouraged to uncomment relevant tests when exploring specific features.

## How to Use the SDK

For detailed instructions on how to use the IXO Spatial Web Multiclient SDK, please refer to the [README.md file on GitHub](https://github.com/ixofoundation/ixo-multiclient-sdk/blob/84f31673e9ea2ada7f31175bc665a54d238e1601/README.md#api). The README provides comprehensive guidance on installing, setting up, creating and signing transactions, as well as querying the blockchain state.

## Use Cases for the SDK

The **IXO Spatial Web Multiclient SDK** is highly versatile and can be used for a variety of purposes, including:

- **Building Impact Projects**: Create, manage, and verify impact projects using blockchain-based digital identities.
- **Managing Digital Assets**: Tokenise real-world assets and manage them using the SDK's blockchain capabilities.
- **Developing Decentralised Applications (dApps)**: Integrate the IXO blockchain to create decentralised applications that contribute to social, economic, and environmental impacts.

## Additional Resources

For more information on using the SDK and its capabilities, refer to the following resources:

- **Documentation**: Full technical documentation is available in the GitHub repository, providing detailed explanations and code examples for each feature of the SDK.
- **How-To Guides**: The GitHub repository includes practical guides on how to implement specific features, such as creating entities or interacting with smart contracts.
- **Community Support**: Engage with the IXO community on platforms like Discord for assistance and knowledge sharing.
- **GitHub Repository**: [IXO Multiclient SDK GitHub](https://github.com/ixofoundation/ixo-multiclient-sdk)

Explore the **IXO Spatial Web Multiclient SDK** to bring the power of blockchain to your applications, enabling verifiable, impactful change on a global scale.

