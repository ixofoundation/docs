---
stoplight-id: dl5zrp5weqph5
---

# SignX SDK

The **SignX SDK** offers developers an easy and secure way to integrate mobile-to-web authentication and transaction signing using the IXO blockchain. It orchestrates the interactions between client applications, a mobile app, and a server, simplifying the complexities of authentication, data handling, and multi-transaction processing.

This SDK abstracts intricate blockchain operations, providing a user-friendly interface for securely managing login requests, transactions, and encrypted data exchange. The SignX SDK enhances user experiences by enabling smooth, real-time interaction across multiple platforms, making it an ideal choice for applications that need secure, verified user interactions and blockchain-based transaction management.

## Key Features

### 1. Mobile-to-Web Authentication

The **SignX SDK** enables seamless authentication through a secure QR code mechanism. A client application generates a unique login request, which is encoded into a QR code for the user to scan with the mobile app. This process allows for secure and smooth user authentication across platforms.

- **QR Code Login**: Secure QR-based login for users.
- **Polling Mechanism**: Continuous polling to keep the client application updated in near real-time once the login process is completed.

### 2. Secure Data Handling

The SDK supports secure data handling between the client application and the mobile app. Data is encrypted using AES-256-CBC encryption and securely transmitted via QR code for the mobile app to decrypt and process. This feature is particularly useful for handling sensitive information such as KYC data.

- **Encryption and Decryption**: Ensures the safe transmission of sensitive information.
- **Data Flow Management**: Manages the secure exchange and processing of encrypted data.

### 3. Multi-Transaction Processing

The **SignX SDK** introduces a multi-transaction processing feature through a v2 transaction module, which supports dynamic sessions involving multiple transactions. This approach allows developers to manage a sequence of transactions within a single session, providing enhanced security and a better user experience.

- **Transaction Sessions**: Manage multiple transactions in a single session, each signed and processed sequentially.
- **Long Polling Mechanism**: Efficiently fetches updates on transaction statuses, ensuring timely responses and real-time progress updates.

## Getting Started

The SignX SDK can be easily installed via npm or yarn:

```bash
npm install @ixo/signx-sdk
yarn add @ixo/signx-sdk
```

- **NPM Package**: [SignX SDK](https://www.npmjs.com/package/@ixo/signx-sdk)
- **GitHub Repository**: [SignX SDK GitHub](https://github.com/ixofoundation/ixo-signx)

For detailed guidance on installation, initialization, and using various features of the SignX SDK, please refer to the [API section of the README.md file](https://github.com/ixofoundation/ixo-signx/blob/e2135f79ef4b8c2f3bc5770321e5375a0c981114/README.md#%EF%B8%8F-api-reference).

## Use Cases for the SDK

The **SignX SDK** can be employed in various contexts, such as:

- **Secure User Authentication**: For applications requiring a robust and user-friendly login experience, using QR-based authentication.
- **Data Exchange in dApps**: Securely transmit and process sensitive data, such as identity verification information.
- **Complex Transaction Handling**: Manage multiple sequential transactions efficiently, ensuring data integrity and a streamlined user experience.

## Additional Resources

For more detailed documentation and code examples, please visit the following resources:

- **Developer Guides**: Practical examples and guides on how to use the SignX SDK can be found in the GitHub repository.

The **SignX SDK** offers a streamlined way for developers to integrate secure mobile interactions into their blockchain-based applications, ensuring a high level of security, user convenience, and adaptability.

