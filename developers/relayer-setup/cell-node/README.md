# Cell Node



## Project Data Store \(PDS\)

The PDS requires a number of services on the vm: the pds app, mongo db, cli, rabbitMQ and memcache.

### Installing the PDS

All these services are installed by docker compose. This is available on github: [https://github.com/ixofoundation/ixo-pds](https://github.com/ixofoundation/ixo-pds)

### Configuration

The configuration is maintained in the docker-compose.prod.yml file

* Running bin/start.sh will restart the services and inject any amended configuration
* Running bin/stop.sh will stop the services
* Running bin/purge.sh will remove all docker images and containers

#### PDS App

* PORT=5000
* MONGODB\_URI=mongodb://db:27017/elysian
* MEMCACHE\_URI=cache:11211
* RABITMQ\_URI=amqp://guest:guest@mq:5672?heartbeat=2
* BLOCKCHAIN\_URI\_REST=http://172.20.1.37/api/
* CONFIG=/usr/src/app/config.json
* TEMPLATE\_REPO=https://api.github.com/repos/ixofoundation/schema/contents/
* ETHEREUM\_API=https://mainnet.infura.io/
* ASYM\_CYPHER=aes-256-cbc
* ASYM\_KEY=trustlab.tech
* VALIDISSUERS=did:sov:123456789
* NODEDID=did:sov:123456789

**VALIDISSUERS**

The list of space separated valid issuers are those identities who issue credentials and validate kyc credentials.

**NODEDID**

This is unique value that identifies the PDS. Projects and claims that are created by the PDS will have the NODEDID embedded in the data. 

#### Pol

* RABITMQ\_URI=amqp://guest:guest@mq:5672?heartbeat=2
* BLOCKCHAIN\_URI\_SYNC=http://172.20.1.37:26657/broadcast\_tx\_sync?tx=0x
* BLOCKCHAIN\_URI\_COMMIT=http://172.20.1.37:26657/broadcast\_tx\_sync?tx=0x
* BLOCKCHAIN\_URI\_VALIDATE=http://172.20.1.37:26657/broadcast\_tx\_sync?tx=0x
* POLLTIMER=3000

#### Cli

* MONGODB\_URI=mongodb://db:27017/elysian
* MEMCACHE\_URI=cache:11211
* BLOCKCHAIN\_URI\_REST=http://172.20.1.37/api/

