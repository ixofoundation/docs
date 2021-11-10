---
description: How to Interface with the ixo blockchain SDK
---

# ixo Blockchain Interfaces

The ixo blockhain SDK provides three interfaces for interacting with a node:

* command-line interface
* gRPC interface
* REST interface

Each interface can be used to query the state. The command-line interface can be used to generate, sign, and broadcast transactions, whereas the gRPC and REST interfaces can only be used to broadcast transactions (a transaction needs to be generated and signed either programmatically or using the command-line interface before it can be broadcasted using the gRPC or REST interfaces).

### Command-Line Interface

The most straightforward way to interact with a node is using the command-line interface.

The ixo binary serves as the node client and the application client, meaning the `ixo` binary can be used to both run a node and interact with it. In Quick Start, we started a local node using the `ixo` binary and then interact with that node by submitting queries and transactions.&#x20;

To learn more about the available commands, install ixo and run the following:

```
ixod --help
```

For transaction commands:

```
ixod tx --help
```

For query commands:

```
ixod query --help
```

For more information about the CLI, check out the [Cosmos SDK Documentation](https://docs.cosmos.network/v0.43/run-node/interact-node.html).

### gRPC Interface

[gRPC](https://grpc.io/docs/what-is-grpc/introduction/) is a modern RPC framework that leverages [protocol buffers](https://developers.google.com/protocol-buffers) for encoding requests and responses between a client and service. The ixo blockchain SDK uses gRPC primarily for querying blockchain state (token balances, data signature records, etc). As a client developer, this means you can query the ixo blockchain state directly by using a gRPC library in your programming language of choice, in combination with the ixo blockchain [protobuf definitions](https://github.com/ixofoundation/ixo-blockchain/tree/master/proto) .

In addition to using a gRPC library, you can also use [grpcurl](https://github.com/fullstorydev/grpcurl) - a command-line tool that lets you interact with gRPC servers. If you have a local node running, you can list the protobuf services available using the following command:

```
grpcurl -plaintext localhost:9090 list
```

To execute a call, you can use the following format:

```
grpcurl \
    -plaintext \
    -d '{"address":"<address>"}' \
    localhost:9090 \
    cosmos.bank.v1beta1.Query/AllBalances
```

In some programming languages, you may be able to leverage a pre-existing client library to take care of most of the heavy lifting, including compiling protobuf messages. For javascript/typescript developers, the [ixo Client-SDK](https://github.com/ixofoundation/ixo-client-sdk) (based on [CosmJS](https://github.com/cosmos/cosmjs)) is a good place to start.

For more information about the gRPC interface, check out the [Cosmos SDK Documentation](https://docs.cosmos.network/v0.43/run-node/interact-node.html).

### REST Interface

All gRPC services and methods for the ixo blockchain SDK are available for more convenient REST based queries through [gRPC Gateway](https://github.com/grpc-ecosystem/grpc-gateway).

For example, you can query the balance of an address using the following `curl` command:

```
curl \
    -X GET \
    -H "Content-Type: application/json" \
    http://localhost:1317/cosmos/bank/v1beta1/balances/<address>
```

To interact with the REST interface, make sure you have API server and (optionally) Swagger UI enabled in your `~/.ixo/config/app.toml` file. With Swagger UI enabled, you can go to `http://localhost:1317/swagger/` to read through the OpenAPI documentation.

For more information about the REST interface, check out the [Cosmos SDK Documentation](https://docs.cosmos.network/v0.43/run-node/interact-node.html).

