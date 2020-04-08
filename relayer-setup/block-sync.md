# Explorer \(Block-sync\)

## Block Sync

The block sync requires the block sync app and db, The ixo-cosmos blockchain and the blockchain rest interface also runs on this vm. 

### Installing the Block Sync

These services are built using docker-compose - except for ixo-cosmos \(see above\)

checkout the docker compose file from github: [https://github.com/ixofoundation/ixo-block-sync](https://github.com/ixofoundation/ixo-block-sync)

### Running block-sync

```text
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

### Configuration

The docker compose files contain environmental variables used by the relevant containers:

#### Block Sync

**PORT**

The port that the block sync will listen on e.g. 8080, but will need to be mapped to port 80

**CHAIN\_URI**

This must point to the IP and port of the ixo-cosmos service e.g. 

```text
172.20.1.37:26657
```

**BC\_REST**

This must point to the IP and port of the ixo rest service using the relevant protocol http/https e.g.  

```text
http://172.20.1.37:1317
```

**MONGODB\_URI**

The mongo container should be left as is on the same vm

**NODEDID\_LIST**

Space separated list of NODEDIDs. For Projects and claims included in the blockchain, only those with the listed NODEDIDs will be included in the block\_sync for listing.

#### ixo Rest Service

**ETH\_URL**

The location of the JSON RPC endpoint for the ixo smart contracts : 

```text
https://ropsten.infura.io/sq19XM5Eu2ANGAzwZ4yk
```

**command node**

The node argument must be set to the ixo-cosmos ip and port using the tcp protocol e.g. 

```text
tcp://172.20.1.37:26657
```



