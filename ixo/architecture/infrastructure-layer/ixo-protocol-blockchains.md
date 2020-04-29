---
description: Software infrastructure for the Internet of Impact.
---

# ixo Protocol Blockchains

The ixo blockchain is open-source software to provide computational and data storage infrastructure for the Internet of Impact. This implements open standards to form an inter-operable network of networks. Anyone set up an ixo blockchain based network, which will provide users with a common set of functionality. 

A network running the core ixo blockchain software can fulfil the following functional requirements: 

| Functional Requirement | ixo Blockchain mechanism |
| :--- | :--- |
| Identify agents | Digital Identifiers \(DID\) & Verifiable Credentials |
| Identify cell nodes | Digital Identifiers \(DID\) |
| Identify projects | Digital Identifiers \(DID\) |
| Identify claims | Content Identifiers \(CID\) |
| Revoke identifiers | Distributed revocation list |
| Open knowledge graph | Distributed Hash Table \(DHT\) |
| Locate cell nodes | DNSLink |
| Program state-changes | Virtual Machines |
| Authenticate identifiers | Public Key Infrastructure \(PKI\) |
| Sign messages | Cryptographic keys |
| Validate messages | Validator nodes |
| Verify claims | Oracles |
| Record proofs of state | Merkle DAGs |
| Transfer value | Digital wallets |
| Issue digital assets | Token minting |
| Incentivise network hosts | Gas fees |
| Prevent Byzantine faults | Tendermint consensus |
| Protect against censorship | Distributed validator nodes |
| Protect against tampering | Hashes |
| Protect against spam | Message Validation |
| _And more ... not an exhaustive list_ |  |

## A modular SDK framework

The ixo Blockchain software is modular. Application-specific networks can configure these modules for their purpose, add new modules, or swap-out some of the non-core modules. These modules are written in Go.

### ixo blockchain SDK modules

The purpose of each module is briefly outlined in the table and described in technical detail on the linked pages.

<table>
  <thead>
    <tr>
      <th style="text-align:left">ixo Blockchain SDK Module</th>
      <th style="text-align:left">Purpose</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Alpha Module</td>
      <td style="text-align:left">Calculates project risk scores (Alpha) which provide signals to the Bonds
        module to adjust the pricing of Alpha-Bonds and trigger bond state changes.</td>
    </tr>
    <tr>
      <td style="text-align:left">Bonds Module</td>
      <td style="text-align:left">
        <p>Calculates the buy/sell price and supply of tokens, using configurable
          bonding curve algorithms and other automated market-maker mechanisms.</p>
        <p>Manages the life-cycle of Alpha Bonds.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Cells Module</td>
      <td style="text-align:left">Maintains a registry of Cell Node identifiers, with associated cryptographic
        public key material and DNSLink record of the cell&apos;s hosting location.</td>
    </tr>
    <tr>
      <td style="text-align:left">Claims Module</td>
      <td style="text-align:left">Maintains a registry of Impact Claim digests and claim status, with verification
        proofs.</td>
    </tr>
    <tr>
      <td style="text-align:left">Data Assets Module</td>
      <td style="text-align:left">Maintains a registry of data assets, automates usage rights management
        and IP ownership/control. Data assets include templates, algorithms, evaluation
        methods, datasets, etc.</td>
    </tr>
    <tr>
      <td style="text-align:left">Fees Module</td>
      <td style="text-align:left">Automates billing, accounting, distribution and settlement of fees for
        all digital services delivered through the network.</td>
    </tr>
    <tr>
      <td style="text-align:left">Identity Module</td>
      <td style="text-align:left">Maintains a registry of trusted root identifiers and revocation lists,
        based on Web of Trust principles and complying with W3C specifications
        for digital identifiers and verifiable credentials.</td>
    </tr>
    <tr>
      <td style="text-align:left">Oracles Module</td>
      <td style="text-align:left">
        <p>Maintains a registry of oracles, with staking and insurance mechanisms.</p>
        <p>Defines rights for oracles to perform specific functions, such as mint
          or burn digital assets (using Object Capabilities).</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Treasury Module</td>
      <td style="text-align:left">Issues standard digital assets through mint and burn functions. Maintains
        a ledger of assets.</td>
    </tr>
  </tbody>
</table>

## Built using the Cosmos-SDK framework 

The ixo blockchain SDK shares a set of core blockchain modules with the Cosmos-SDK and is built using the same standards. The Cosmos-SDK is a software development kit for building application-specific blockchains. 

This enables functional interoperability between blockchains that implement the same modules.  

For example: 

* The `MsgSend` function transfers fungible tokens of designated denominations between counter-parties, using the `bank module`.  
* The `account`querier function, which is part of the `Auth Module`, returns information about an account, regardless of which chain this account is created on. 
* The `IBC module`enables messages to be sent between blockchain networks implementing the [Inter-Blockchain Communication Protocol](https://cosmos.network/ibc).  

