---
description: ⚠️ PAGE UNDER CONSTRUCTION
---

# ixo Entities

An Entity is a node in the Internet of Impact graph. The best way of explaining this is to describe the different classes of entities and their primary puposes.

| Entity Class | Primary Purpose |
| :--- | :--- |
| Agent | The digital representation of a natural person, organisation, machine, or software service. |
| Cell | The cybernetic unit of organisation for coordinating a network of Agents. |
| Project | The operational unit for Agents to perform tasks that can be recorded as digital claims. |
| Investment | The economic unit for programming resource-flows between Agents. |
| Oracle | A service that operates on stateful data to provide precision functions \(P-functions\). |
| Data Asset | The digital representation of any type of data that can be used in a data marketplace transaction. |
| Template | The generic instance of an entity, which can be used to create a specific instance of the entity.  |

Entities are inter-linked. The relationships between entities are the edges of the impact graph, as illustrated in the example below.

 {insert diagram}

{% hint style="info" %}
Each entity has its own digital identifier, in the format `did:ixo:29wribufwiuw984feuf98348fj9f4`and an associated stateful digital record, which is referred to as the DID Document \(DDO\).
{% endhint %}

{% hint style="info" %}
**User Story**

As a user of the Internet of Impact,  I am an Agent with a digital identifier that I can authenticate with keys that are stored in my Impact Wallet, over which only I have control. As an Agent, I can create a cyber-cellular organisaton \(Cell\) to coordinate the activities of other agents, such as the members of my team, towards achieving a shared mission. I associate the cell with a Cell-node, which provides computational and data hosting infrastructure for the cell and its related entities. Now members of my cell can create one of more Projects. The simplest way of doing this is by using a Template. I can set up an investment entity to form and allocate resources to the cell and projects, using an instrument such an Alpha-bond. I can employ oracles to assist with a range of precision functions. If I have data assets that will be used by my own and other entities, I can register this and make it avalailable in a data marketplace. All information and transactions flow between these entities in the format of cryptographically signed messages between identified counter-parties. 
{% endhint %}

