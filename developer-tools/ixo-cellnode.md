


## ixo-cellnode node setup

ixo-blocksync syncs all the public info from the ixo blockchain to mongodb

### Infrastructure requirements

* Ubuntu 18.04 OS
* 2 CPUs
* 4 GB RAM
* 75GB SSD
* Static IP address


#### Install dependencies as root user: 


```text
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common build-essential libssl-dev python make gcc libssl-dev git containerd -y
sudo apt-get install docker-ce docker-ce-cli -y
sudo usermod -a -G docker ixo
sudo apt update
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

#### Set up IXO-cellnode: 

```text
git clone https://github.com/ixofoundation/ixo-cellnode.git # or clone your own fork
cd ixo-cellnode/


```

Update the following variables in docker-compose.yml
```
BLOCKCHAIN_URI_REST=http://<blocksync IP>/api/did/getByDid/
BLOCKSYNC_URI_REST==http://<blocksync IP>/api/
```

Run the Docker containers
```text
cd bin
./start.sh
```

Change credentials of Mongo. Any changes must be reflected in the docker-compose.yml file.

Access the docker container:
```text
docker exec -ti db /bin/bash
```

Update the user credentials.
```
mongod

use admin

db.createUser({user: "<admin username>", pwd: "<admin password>", roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]})

db.auth("<admin username>", "<admin password>" )

exit

mongo --port 27017 -u "<admin username>" -p "<admin password>" --authenticationDatabase "admin"

use elysian

db.createUser({user: "<username>", pwd: "<password>", roles: [{role: "readWrite", db: "elysian"}]})
```


