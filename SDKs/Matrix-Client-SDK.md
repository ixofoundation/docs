---
stoplight-id: kfgcjfmlnwy2n
---

# IXO Matrix Client SDK Overview

The **IXO Matrix Client SDK** is a comprehensive toolkit that enables developers to interact seamlessly with a Matrix server and associated bot services. This SDK helps in managing user profiles, room details, and room states, leveraging both pre-configured and custom Matrix home servers. It is ideal for applications that require secure, real-time communication and data handling across multiple rooms and users.

## Overview

The **IXO Matrix Client SDK** provides the following capabilities:

- **User Profile Management**: Query and update user information, including display names and avatars.
- **Room Management**: Create, join, leave, and manage room properties, such as visibility and membership.
- **Bot-Assisted Room Automation**: Automate entity room management, set access control lists (ACLs), and handle room state using bot clients.
- **Developer Utilities**: Utility functions for handling MXC URLs, validating inputs, and facilitating interaction with Matrix rooms and profiles.

## Key Features

### 1. Matrix API Client

The **Matrix API Client** facilitates direct interaction with the Matrix API to manage media, user profiles, and room properties. Key features include:

- **Media Management**: Upload files to the Matrix server, making them publicly accessible through the content repository.
- **User Profile Handling**: Retrieve and modify user profile data, such as display names and avatars.
- **Room Operations**: Manage room visibility, join or leave rooms, and handle room memberships.

### 2. Room Bot Client

The **Room Bot Client** provides automation capabilities for managing rooms, enabling developers to simplify workflows involving room creation and membership.

- **Entity Room Management**: Automatically create entity-specific rooms, invite users, and handle memberships as needed.
- **Room Automation**: Use bots to efficiently manage room invitations and memberships.

### 3. State Bot Client

The **State Bot Client** is used for handling room states and access control lists (ACLs), ensuring secure and organized management of room-level configurations.

- **Access Control Management**: Retrieve and configure ACLs for rooms, defining who can access or modify room content.
- **State Management**: Fetch and adjust room states to maintain configurations and ensure room consistency.

### 4. Utility Functions

The SDK also provides several utility functions that assist developers working within the Matrix ecosystem:

- **MXC Utilities**: Convert Matrix Content (MXC) URLs to standard HTTP URLs.
- **Validators**: Validate room IDs, user IDs, aliases, and MXC links to ensure compliance with required standards.

## Getting Started

The **IXO Matrix Client SDK** can be installed via npm or yarn:

```bash
npm install @ixo/matrixclient-sdk
yarn add @ixo/matrixclient-sdk
```

- **NPM Package**: [IXO Matrix Client SDK](https://www.npmjs.com/package/@ixo/matrixclient-sdk)
- **GitHub Repository**: [IXO Matrix Client SDK GitHub*](https://github.com/ixofoundation/ixo-matrixclient-sdk)

To get started, import the required components into your project:

```typescript
import {
  createMatrixApiClient,
  createMatrixRoomBotClient,
  createMatrixStateBotClient,
  utils
} from '@ixo/matrixclient-sdk';
```

For detailed information on usage and examples, refer to the [README.md file*](https://github.com/ixofoundation/ixo-matrixclient-sdk/blob/main/README.md).

## Use Cases for the SDK

The **IXO Matrix Client SDK** is highly versatile and can be used in multiple scenarios, such as:

- **Real-Time Communication**: Manage real-time user communication using Matrix rooms for secure, reliable interaction.
- **Automated Room Management**: Leverage bot clients to automate the creation, configuration, and management of entity rooms.
- **Access Control**: Use ACLs and state management tools to control and secure room access, ensuring data safety.

The **IXO Matrix Client SDK** equips developers with the tools needed to create secure, scalable, and well-integrated applications that take full advantage of the Matrix ecosystem, enabling effective real-time communication and management of decentralized rooms and services.

<!-- theme:info -->
> Note:
> This Github repository is private. Request access by contacting the IXO World team.
