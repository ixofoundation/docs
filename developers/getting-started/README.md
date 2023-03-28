---
description: The Impact blockchain for the Cosmos ecosystem
---

# ixo Blockchain

These instructions allow you to run a single node network on your local machine and interact with it using the command line interface (CLI). It is the simplest way to become familiar with the ixo Blockchain.

After completing this guide you can [run a node](https://github.com/ixofoundation/genesis/blob/main/README.md) on the `pandora` testnet.

{% hint style="info" %}
We recommend the use of Docker and Docker Compose. The configuration files are provided in the `ixo-blockchain` directory.
{% endhint %}

{% hint style="info" %}
Another way to interact with a node is the [ixo MultiClient SDK](../ixo-multiclient-sdk/), instead of CLI.
{% endhint %}

### Prerequisites

You will need the following to install and run the `ixo` binary:

* [Git](https://git-scm.com/) `>=2`
* [Make](https://www.gnu.org/software/make/) `>=4`
* [Go](https://golang.org/) `>=1.19`

Optional:

* [Docker](https://docs.docker.com/engine/install/)&#x20;
* [Docker Compose](https://docs.docker.com/compose/install/)

### Install ixo

The `ixo` binary is named `ixod` and serves as the node client and the application client. In other words, the `ixo` binary can be used to both run a node and to interact with it.

Clone the `ixo` repository:

```bash
git clone https://github.com/ixofoundation/ixo-blockchain.git
```

Change to the `ixo-blockchain` directory:

```bash
cd ixo-blockchain
```

Check out the latest stable version:

```bash
git checkout main
```

{% tabs %}
{% tab title="Local" %}
#### Run a node

Start a session (let's refer to it as `session 1`).

Install the `ixo` binary.

```bash
#session 1
make install
```

Check to make sure the installation was successful.

```bash
ixod version
```

Start the `ixo-blockchain` node using pre-configured data.

```bash
./scripts/run_with_all_data.sh
```

{% hint style="info" %}
The script will start the blockchain and create accounts appropriate for the `ixo-blockchain` to enable easy interaction. The blocks will progress and you should see the logs to confirm it.
{% endhint %}

#### Interact with the node

Start another session (let's refer to it as `session 2`).

Use the `ixod` CLI to query the total bank balances.

```bash
# session 2
ixod query bank total
```

You can now interact successfully with the `ixo` binary.

#### Stop and restart the node

Go back to `session 1`.

Stop the running node using `CTRL` + `C`.

There are two ways to restart the node:

1. With the same data and continuing from the same block height.

```bash
ixod start
```

2. or with the data reset to the first time the node started successfully and from block height 1.

```bash
make run_with_all_data
```
{% endtab %}

{% tab title="Docker" %}
#### Run a node

Create a Docker image called `ixo-chain`and tagged `devel`.

```bash
docker build -f .infra/dockerfiles/Dockerfile -t ixo-chain:devel .
```

Compose a Docker container.

```bash
docker-compose up -d --build
```

Start a Bash session (let's refer to it as `bash session 1`).

```bash
# bash session 1
docker exec -it ixo_blockchain bash
```

Install the `ixo` binary.

```bash
make install
```

Check to make sure the installation was successful.

```bash
ixod version
```

Start the `ixo-blockchain` node using pre-configured data.

```bash
./scripts/run_with_all_data.sh
```

{% hint style="info" %}
Script will start the blockchain and create accounts appropriate for the `ixo-blockchain` to enable easy interaction. The blocks will progress and you should see the logs to confirm it.
{% endhint %}

#### Interact with the node

Start another Bash session (let's refer to it as `bash session 2`).

```bash
# bash session 2
docker exec -it ixo_blockchain bash
```

Use the `ixod` CLI to query the total bank balances.

```bash
ixod query bank total
```

You can now interact successfully with the `ixo` binary.

#### Stop and restart the node

Go back to `bash session 1`.

Stop the running node using `CTRL` + `C`.bash

There are two ways to restart the node:

1. With the same data and continuing from the same block height.

```bash
ixod start
```

2. or with the data reset to the first time the node started successfully and from block height 1.

```bash
make run_with_all_data
```
{% endtab %}
{% endtabs %}

