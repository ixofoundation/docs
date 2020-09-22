---
description: Guide for setting up a Relayer on the Pandora Test Network.
---

# Join a Test Network

## Purpose of the Test Network

The Pandora Test Network is the precursor to launching the Sustainability Hub. This tests the functioning of a bonded proof of stake network which deploys the latest upgrades of Tendermint Core, the Cosmos SDK modules and ixo Modules.

Joining this test network enables you to experience how ixo Validator Nodes operate, test your hardware configuration before joining the main network, try out the functionality of an ixo protocol network and build applications for the network.

Setting up your own validator node on the test network is permissionless and does not require any economic stake. However, please contact the ixo team [on Telegram](https://t.me/ixotestnet) to check the latest status of the network and to get any support you may need. 

## Relayer components

Setting up a fully operational Relayer on the Pandora Testnet requires deploying the following components:

1. `ixo-blockchain` validator node.
2. `ixo-blocksync` caching database
3. `ixo-apimodule` node.js API module
4. `ixo-cellnode` decentralised data cell container
5. `ixo-webclient` React web application
6. `ixo-keysafe` Chrome browser extension keystore
