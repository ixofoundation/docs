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

## 1. ixo-blockchain Validator node setup

### Infrastructure requirements

* Ubuntu 18.04 OS
* 2 CPUs
* 2 GB RAM
* 50GB SSD
* Networking: Allow incoming connections on port 26656
* Static IP address

### Installation

The installation script `InstallPandora.sh` prepares the environment, prerequisites, installs the ixo-blockchain software and guides you through the node setup.

These steps are to be run once logged in as **root** user. Use the following command to access the root user.

```text
sudo -i
```

Install git to clone this repository on the VM

```text
apt-get install git
```

Access the root user's home directory and clone the repository

```text
cd $HOME
git clone https://www.github.com/franono/genesis.git && git checkout master
```

The pandora-1 directory includes: 

* The network genesis fille with pandora-1 network details, parameters and starting data. 
* `InstallPandora.sh` which is to be run in the next step to install all the requirements and blockchain software to participate in the network.

Access the pandora-1 folder and run the installation script.

```text
cd pandora-1
bash InstallPandora.sh
```

This script goes through the following steps:

1. Installs Golang 1.13.8, make, gcc and curl.
2. Updates and upgrades Ubuntu packages.
3. Prompts user to create a new IXO non-sudo user to run the software with.
4. Sets required environmental variables for Golang.
5. Clones the ixo-cosmos repo at the specific commit of pandora-1, 7ee1d6f268ce0bee281c165eb5c4c9951dcd3229.
6. Creates the directories required for the ixo node configurations and blockchain data.
7. Installs the IXO blockchain daemon and CLI tool
8. Configures the node to use pandora-1's genesis file.
9. Creates and an enables a systemd service with which the IXO node daemon will be run.

Follow the configuration steps as the node is installed.

Switch to the new IXO user

```text
su ixo
```

Access the node's configuration file and add Simply VC's Pandora-1 peers.

```text
nano $HOME/.ixod/config.toml
```

**Required**: Find the `persistent_peers` parameter and add the following peers to it's value.

The default value of this entry should be "". This must be changed to look as follows:

```text
"6098df32ec7e5b859032a9f22e415de0f369fbaf@46.166.138.209:26656,19690fa3856dd9d9398c59c7a1eb8bb63fd19683@80.64.208.22:26656"
```

**Required**: Enable the peer exchange reactor `pex`, which enables nodes to share each other's peers. This ensures your node discovers other peers on the network.

The default value of this entry should be "false". This must be changed to look as follows:

```text
pex = true 
```

**Optiona**l: The node's moniker can be changed from `Pandora node` to anything of your liking.

The default value of the `moniker` entry is `"Pandora node".` This can be changed as desired.

Start the IXO blockchain daemon.

```text
systemctl start ixod.service
```

Check the node's logs as the root use

Switch to the root user. This can be done by exiting the current user's shell instance.

```text
exit
```

Tail the node's logs using the following:

```text
journalctl -f -u ixod.service
```

Ensure the node is receiving and processing blocks, which would look like below.

```text
Executed block    module=state height=20 validTxs=0 invalidTxs=0
Committed state   module=state height=20 txs=0 appHash=3A6BB8049C10D0FB3C9C58A85B8FD840BBD28BDDCB8566621FEDFAB240C2FB5C
```

If all these steps were completed successfully, the node should be syncing through the whole Pandora-1 blockchain. 

Should you have any issues, please [contact ixo support on Telegram](https://t.me/ixotestnet).

**Final steps**:

1. Backup the generated `priv_validator_key.json` stored in `$HOME/.ixod/config/`, which is the validator's block/consensus signing key.
2. Obtain the node's peer ID and IP for sharing with other node operators.

```text
# Obtain the node's peering ID
ixod tendermint show-node-id

# Obtain the node's public IP
curl https://ipinfo.io/ip
```

4. Create an address to receive testnet tokens on.

You will be prompted to enter a password and then save/backup a seed phrase.

```
ixocli keys add validator
```

Once this has been generated, run the following command and take note of the `address` field, which will contain your address.

```
ixocli keys list
```

Submit this to the IXO testnet support Telegram chat to receive testnet tokens.

4. Register your validator on-chain `create-validator` command.

Once you have received tokens, you can go ahead and send transactions on the network. Registering your validator to participate in the network's consensus comprises of sending a transaction that will register your software's identity on the network, and it's rights to sign/vote on the blocks/transactions that are being processed.
```
ixocli tx staking create-validator   --amount=1000000stake   --pubkey=$(ixod tendermint show-validator)   --moniker="<Enter a validator name here>"   --trust-node=true   --commission-rate="0.10"   --commission-max-rate="0.20"   --commission-max-change-rate="0.01"   --min-self-delegation="1"   --gas="auto"   --gas-prices="0.025stake"   --from=validator
```


