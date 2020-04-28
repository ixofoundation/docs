---
description: How to configure a Matrix App for your node
---

# Matrix App

## Matrix App Setup

Adding a Matrix app to your cell enables you to organise collaboration rooms for your agents, teams and community. Matrix provides chat, file-sharing, video/voice calls, group conferencing and more.

You can create rooms with different topics and membership groups for your cell and for each of your projects.

#### What your authorised agents and public users will experience.

The default Matrix Client used by ixo.world is Riot Chat. This has been described as the open-source alternative to Slack. When your user clicks on the Riot app badge in the Control Panel of your cell or project, this opens up an external window that directly brings the user into the default piublic and private rooms for your cell or project.

The default room ID is the DID of your cell or project, which gets automatically created for you. You may choose to create additional human-readible aliases for your room, using the Riot client.

#### Integrations connecting out from your node.

Matrix bridges across to other popular communications and collaboration platforms. This means that your users can channel data and messages to or from the tools they already use and love, including platforms such as Slack and Discord. This brings your cell and projects into your users' chosen collaboration environment/s and workflows.

#### Where your communications data get stored

By default, this Matrix app is configured to use a server hosted by ixo.world, which is physically located in the EU on the island of Malta. The URL of this server is [https://comms.ixo.world](https://comms.ixo.world/)

This server has been customised to use DID-Auth for security and convenience \(so there is no need for separate user names and passwords!\). However, you may choose to change your hosting to any other matrix server and you can port all your data if you choose to move servers.

To configure this App for your cell or for each of your projects, you must first connect to the Matrix server. This guideline will describe the process for the ixo.world server. For other servers, see the Matrix documentation.

#### How to configure the Matrix app for your users.

To register as a Matrix user, you will authenticate into the Matrix server at comms.ixo.world, using your ixo Keysafe \(or ixo Mobile Wallet\) to sign in. If you have already registered previously using your DID \(or !id\), just go ahead and sign in.

Now you will be requested to configure:

* The room topic
* Whether to provision a public room that anyone can access
* Whether to provision a private room that is by invitation only
* If members of the private room are permitted to invite new members

After submitting these settings, you are done!

The Riot app will now appear in the Control Panel for your cell or project, ready for your agents and community to start communicating!

For more guidance on how to use the powerful features of Matrix, from within the Riot client, see this documentation.

To remove this App from your cell or project and to change the configuration settings, return to the App configuration panel.

#### Security and privacy

Matrix implements state of the art end-to-end encryption to ensure that your private communications remain private.

