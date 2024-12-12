---
stoplight-id: wx09lei4xl255
---

# IXO Matrix State Bot API

The **IXO Matrix State Bot API** is an open-source solution designed for managing state objects within the Impacts Matrix Rooms of the IXO ecosystem. By leveraging the Matrix protocol, this bot enables secure, decentralised storage and management of state events and access control lists (ACLs) for applications, projects, and communities. The API provides both Matrix commands and a RESTful interface for managing state and ACL events efficiently, making it a versatile tool for developers looking to integrate stateful interactions into their decentralised applications (dApps).

## Purpose of the API

The core purpose of the **IXO Matrix State Bot API** is to enable developers to manage room-specific settings, configurations, and stateful data securely and seamlessly within the Impacts Matrix ecosystem. By abstracting the complexities of Matrix server interactions, the API empowers users to:

- Create, read, update, and manage state objects.
- Define and manage ACLs to control access and permissions.
- Automate state management tasks using a REST API or Matrix commands.

## Key Features

### 1. Custom State Event Management

The API allows developers to define, store, and manage custom state events in Impacts Matrix Rooms. Each state event can hold application-specific data, stored under unique keys (`state_key`) for organised and secure access.

- **State Events (`ixo.room.state`)**: Represent room settings or configurations, stored as JSON objects.
- **ACL Events (`ixo.room.state.acl`)**: Define access permissions for state events, ensuring secure data interactions.

### 2. Flexible Access Control

Developers can use ACLs to set granular access and edit permissions for room-specific state events. ACLs are directly tied to the corresponding state events, providing robust security for decentralised applications.

### 3. REST API Integration

The RESTful interface offers a direct way to interact with the bot for managing state and ACL events. It simplifies backend integrations by providing endpoints for:

- Fetching and updating state events.
- Managing ACLs.
- Inviting the bot to rooms and configuring its access levels.

### 4. Matrix Commands

The bot also supports Matrix room commands for managing state and ACL events within the Matrix ecosystem. These commands offer a quick and intuitive way to perform state-related tasks directly in chat rooms.

## Use Cases

The **IXO Matrix State Bot API** is suitable for a variety of applications, including:

- **Decentralised Application Settings**: Store and manage application-specific configurations securely within Matrix rooms.
- **Access Control for Projects**: Implement fine-grained ACLs for managing permissions within collaborative projects.
- **Real-Time State Management**: Automate the management of state objects in decentralised environments.

## Additional Resources

For more detailed documentation and examples, visit the GitHub repository:

- **GitHub Repository**: [IXO Matrix State Bot](https://github.com/ixofoundation/ixo-matrix-state)

<!-- theme: info --> 
> This repository is private. [Reach out to us](https://linktr.ee/ixo_world) to be added as a contributor. 

The **IXO Matrix State Bot API** provides a powerful and flexible platform for managing stateful interactions within the IXO ecosystem, enabling developers to build secure, decentralised solutions that scale with their needs.



