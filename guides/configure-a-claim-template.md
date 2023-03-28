---
description: ⚠️ PAGE UNDER CONSTRUCTION
---

# Configure a Claim Template

The simplest way to start configuring a claim template is to use a pre-existing template as the basis. Templates can be found in the Templates Explorer section of the ixo-webclient.

To create a [new Claim Template](https://app.ixo.world/template/new/template) from scratch, you can ask the ixo-assistant to guide you through the process by asking something like "I want to create a new Service Claim template". This will open up the relevant page in the ixo-webclient where you can complete the claim template setup using the configuration form.

Every claim template has three sections, with associated objects:

1. **Form fields**, which includes the following types of cards:

* Short text
* Long Text
* Multiple-choice
* Radio button
* Photo capture / image upload
* Picture selector
* Sliding scale
* Video capture / file upload
* Sound recording / file upload
* Document scan / file upload
* QR code scan
* Email with validation
* Mobile phone with validation
* Identity and credential with validation
* Profile photo for identity verification

1. **Settings**, which includes metadata about the claim template:

* Creator
* Owner
* Status
* Version
* Terms of Use
* Privacy Settings
* Privacy Credentials
* Filters
* Display Credentials
* Embedded Analytics

1. **Advanced Settings**

* Linked Entities
* Payments
* Staking
* Nodes
* Funding
* Keys
* Services
* Data

Verifiable Claims are defined as a [JSON Schema](../ixo/developers/developer-tools/schema-server/data-asset-schema/) using JSON-LD.
