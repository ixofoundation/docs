---
description: API Access Calls to the IXO Block Sync
---

# API's

Interfaces are available for each of the components module of the ixo-SDK

* ixo-apiModule \(NPM module\)
* ixo-blocksync \(Blockchain Explorer\)
* ixo-cellNode \(Decentralised Data Store\)
* ixo-blockchain \(Validator Node\)
* ixo-Keysafe \(Chrome browser extension\)

## ixo-apiModule API

This NPM module provides APIs that simplify interacts between the ixo-SDK user interfaces and Cell Nodes, Blockchain Nodes and blocksync.

`npm install --save ixo-module`

To Create a new ixo Object \(Without provider\)

```text
import ixo from 'ixo-module';
var ixo = new ixo('ixo_node_url')
```

NOTE

### Entity Functions

Functions are called using `ixo.project.<functionName>` // In future, this will be replaced with the more generic `ixo.entity.<functionName>`

#### List Entities

Returns a list of all entities cached in the Explorer Node \(ixo-blocksync\). Note that each ixo Relayer Portal can configure their instance of ixo-blocksync to only synchronise entities that are associated with the Relayer. Linked entities have the Relayer Node-ID in their blockchain record \(Entity Document\).

Request:

```text
ixo.project.listProjects().then((result) => {
    console.log('Project List: ' + result)
})
```

Response: [ixo Explorer: listProjects](api.md#explorer-listProjects)

#### Get Project

Retrieves public project details by DID

```text
let projectDid = 'did:ixo:TknEju4pjyRQvVehivZ82x';
ixo.project.getProjectByDid(projectDid).then((result) => {
    console.log('Project Details: ' + result)
})
```

Response: [ixo Explorer: getProject](api.md#explorer-getProject)

#### Create Project

```text
ixo.project.createProject(projectData, signature, PDSUrl).then((result) => {
    console.log('Project Details: ' + result)
})
```

Response: [ixo-cellNode: createProject](api.md#pds-createProject)

#### Upload Public Data

Function to upload into a Cell Node any public content relating to an entity. This returns a unique content identifier \(CID\) for the data. This allows the data to be content-addressed and retrieved using the identifier `dataUrl`. The primary use is to upload images and json template files to the Cell Node. But this can accept any arbitrary project-specific public data.

The `dataUrl` takes the form of `data:<mediatype>;<encoding>,<data>` // In future this will be replaced by IPLD standard content addresses

```text
// Upload an image
let dataUrl = 'data:image/png;base64, iVBORw0KGgoAAAANSUhEUgAAAAUA AAAFCAYAAACNbyblAAAAHElEQVQI12P4//8/w38GIAXDIBKE0DHxgljNBAAO 9TXL0Y4OHwAAAABJRU5ErkJggg==';
ixo.project.createPublic(dataUrl, PDSUrl) {
    console.log('Document hash: ' + result)
})
```

Response: [ixo-cellNode: createPublic](api.md#pds-createPublic-image)

#### Retrieve Public Data

Retrieves previously uploaded data from a Cell-Node using the content address \(hash\)

```text
ixo.project.fetchPublic(documentHash, PDSUrl) {
    console.log('Document hash: ' + result)
})
```

Response: [ixo-cellNode: fetchPublic](api.md#pds-fetchPublic-image)

### Agent Functions

These calls take the form `ixo.agent.<functionName>`

#### List Agents

Returns a list of all agents associated with an entity, from the Cell Node.

Request:

```text
ixo.agent.listAgentsForProject(data, signature, PDSUrl).then((result) => {
    console.log('Agent List: ' + result)
})
```

Response: [ixo-CellNode: listAgents](api.md#pds-listAgents)

#### Register an Agent for an Entity

Associates the Agent DID with the entity.

Request:

```text
ixo.agent.createAgent(agentData, signature, PDSUrl).then((result) => {
    console.log('Create Agent: ' + result)
})
```

Response: [ixo-cellNode: createAgent](api.md#pds-createAgent)

#### Update Agent Status

Update an agent's registration status.

Valid statuses are:

| Status | Value |
| :--- | :--- |
| Pending | 0 |
| Approved | 1 |
| Revoked | 2 |

Request:

```text
ixo.agent.createAgent(agentData, signature, PDSUrl).then((result) => {
    console.log('Update Agent Status: ' + result)
})
```

Response: [ixo-cellNode: updateAgentStatus](api.md#pds-updateAgentStatus)

### Claim Functions

Calls take the form `ixo.claim.<functionName>`

#### List Claims

Returns a list of all claims for an entity, from a Cell Node, together with the claim status.

Request:

```text
ixo.claim.listClaimsForProject(data, signature, PDSUrl).then((result) => {
    console.log('Claim List: ' + result)
})
```

Response: [ixo-cellNode: listClaimsForProject](api.md#pds-listClaimsForProject)

#### List Claims by Template ID

Returns a list of filtered claims for an entity, from a Cell Node, together with the claim status. Claims are filtered by a template ID expected to be included in `data` as `claimTemplateId`.

Request:

```text
ixo.claim.listClaimsForProjectByTemplateId(data, signature, PDSUrl).then((result) => {
    console.log('Claim List: ' + result)
})
```

Response: [ixo-cellNode: listClaimsForProjectByTemplateId](api.md#pds-listClaimsForProjectByTemplateId)

#### Issue Claim

Issues a claim for an entity.

Request:

```text
ixo.agent.createClaim(agentData, signature, PDSUrl).then((result) => {
    console.log('Create Claim: ' + result)
})
```

Response: [ixo-cellNode: createClaim](api.md#pds-createClaim)

#### Evaluate a Claim

Sets the evaluation status for a claim.

Valid statuses are:

| Status | Value |
| :--- | :--- |
| Pending | 0 |
| Approved | 1 |
| Rejected | 2 |

Request:

```text
ixo.agent.evaluateClaim(evaluationData, signature, PDSUrl).then((result) => {
    console.log('Create Evaluation: ' + result)
})
```

Response: [ixo-cellNode: evaluateClaim](api.md#pds-evaluateClaim)

### User Functions

#### Register agent DID and DID Document

Registers a new agent identifier and DID document \(DDO\) to the ixo blockchain.

Request:

```text
ixo.user.registerUserDid().then((result) => {
    console.log('Register DID: ' + result)
})
```

Response: [ixo Blockchain: registerUserDid](api.md#blockchain-registerUserDid)

#### Get a DID Document

Retrieves the DID Doc for a specified agent identifier

Request:

```text
Let did = 'did:sov:2p19P17cr6XavfMJ8htYSS';
ixo.user.getDidDoc(did).then((result) => {
    console.log('DID Doc: ' + result)
})
```

Response: [ixo Blockchain: getDidDoc](api.md#blockchain-getDidDoc)

### Metrics

Returns the global statistics for all entities associated with a Relayer node.

Request:

```text
ixo.stats.getGlobalStats().then((result) => {
    console.log('Statistics: ' + result)
})
```

Response: [ixo Explorer: getGlobalStats](api.md#explorer-getGlobalStats)

### Health Check Functions

#### Blockchain Health Check

Request:

```text
ixo.network.pingIxoBlockchain().then((result) => {
    console.log('Health Check: ' + result)
})
```

Response: [ixo Blockchain: healthCheck](api.md#blockchain-health)

#### Explorer node health check

Request:

```text
ixo.network.pingIxoExplorer().then((result) => {
    console.log('Health Check: ' + result)
})
```

Response: [ixo Explorer: ping](api.md#explorer-ping)

## Keysafe Browser Extension API

When the keysafe extension operates through the browser `window` object.  
This can be accessed as follows:

```text
const IxoInpageProvider = window['ixoKs'];
let keysafe = new IxoInpageProvider();
```

### Information Functions

#### Get User Information

Returns a javascript object containing a user name and associated DID Document from the keysafe local store.

Request:

```text
keysafe.getInfo().then((error, result) => {
    if (result) {
        console.log('User Info: ' + result)
    } else {
        console.log(error)
    }
})
```

Response:

```text
{
    name: "John",
    didDoc: {
        "did": "did.ixo.EvBFmtyRaBuMNMnwjHNVgn",
        "pubKey": "8awT75ZgZttei45J52bcXC2q8isMRATLcdgbmx4FHyFf"
    }
}
```

#### Get User DID Doc

Returns a javascript object containing the user's DID Doc from the local store.

Request:

```text
keysafe.getDidDoc().then((error, result) => {
    if (result) {
        console.log('User DID Doc: ' + result)
    } else {
        console.log(error)
    }
})
```

Response:

```text
{
  "did": "did:ixo:2HQrdvfjqZwRQCapLDPZzY",
  "pubKey": "hZHiC5kPgiADRXnuiktvmsNSPH1D4c96NxMSjjNLVTY",
}
```

### Signing Functions

#### Request Signing

Request the user to sign some data using their keys in the keysafe wallet.

```text
keysafe.requestSigning(JSON.stringify(data), (error, signature) => {    
    if (!error) {
        console.log("Signature: " + signature);
    } else {
        console.log(error);
    }
});
```

Response:

`A011D11A2D91A9CB03ECFFB7D9AFC1001DB56B3DABF42BDD0F4D00352A9B8E0E73E85F0B4586DA2934696C0A78602EEB047EA6B3D9096C1A0C3FB144E6A51C09`

## Cell Node API

Note: the legacy name for Cell Node was Project Data Store \(PDS\).

A Cell Node is a decentralised data processing and storage node. This has a public API and private API. Public API requests do not require cryptographic signatures. All other requests must be signed and adhere to the capabilities that have been granted to the signer.

### Public API

URI: `<pds server>/api/public`

Request type: `POST`

Structure: `{"jsonrpc": "2.0", "method": "<method name>", "id": <message id>, "params": <json data object> }`

| Variable | Description |
| :--- | :--- |
| `<node server>` | The URL of the server |
| `<entity>` | The entity to send the method |
| `<method name>` | The name of the method to call defined in the config file |
| `<message id>` | The message ID, used to correlate asynchronous responses |
| `<json data object>` | The parameters that are passed to the method handler |

#### Structure of the params object

These are unsigned requests for publicly available information. A content identifier is generated and sent back to the client, to be used in retrieval of this information.

Data will be accepted any of the following encodings: "ascii" \| "utf8" \| "utf16le" \| "ucs2" \| "base64" \| "latin1" \| "binary" \| "hex".

contentType should reference a MIME type. See [https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics\_of\_HTTP/MIME\_types/Complete\_list\_of\_MIME\_types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Complete_list_of_MIME_types)

```text
{
    "jsonrpc":"2.0", 
    "method":"createPublic",
    "id": 123,
    "params": {
        "data": "bob public message", 
        "contentType": "text"
        }
}
```

`<a name="pds-createPublic-image"></a>`

#### Upload an image

Request:

```text
{
    "jsonrpc": "2.0", 
    "method": "createPublic", 
    "id": 3, 
    "params": 
        {
        "data": "<base64 encoded image>", 
        "contentType": "image/png"
        }
}
```

Response:

```text
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": "<string>"
}
```

#### Fetch image

Request:

```text
{
    "jsonrpc": "2.0", 
     "method": "fetchPublic", 
     "id": 3, 
     "params": {"key": <string>}
}
```

Response:

```text
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": {
        "data": "<base64 encoded image>",
        "contentType": "image/png"
    }
}
```

#### Upload a Json file

Request:

```text
{
     "jsonrpc": "2.0", 
     "method": "createPublic", 
     "id": 3, 
     "params": 
    {
       "data": "<JSON string>", 
       "contentType": "application/json"
    }
}
```

Response:

```text
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": "<string>"
}
```

#### Fetch Json file

Request:

```text
{
    "jsonrpc": "2.0", 
     "method": "fetchPublic", 
     "id": 3, 
     "params": {"key": <string>}
}
```

Response:

```text
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": {
        "data": "<JSON string>",
        "contentType": "application/json"
    }
}
```

### Private API

URI: `<pds server>/api/request`

Request type: `POST`

Structure: `{"jsonrpc": "2.0", "method": "<method name>", "id": <message id>, "params": <json data object> }`

| Variable | Description |
| :--- | :--- |
| `<node server>` | The URL of the server |
| `<entity>` | The entity to send the method |
| `<method name>` | The name of the method to call defined in the config file |
| `<message id>` | The message ID, used to correlate asynchronous responses |
| `<json data object>` | The parameters that are passed to the method handler |

#### Structure of the params object

Everything in the payload section is signed to generate a valid signature. This should be packaged using `JSON.stringify()` method before signing.

```text
{
    "jsonrpc":"2.0", 
    "method":"createAgent",
    "id": 123,
    "params": {
        "payload": {

            "template": {
                "name": "create_agent"
            },
            "data": {"projectDid": "did:ixo:TknEju4pjyRQvVehivZ82x",
                     "name": "Brennon",
                     "surname": "Hampton",
                     "email": "brennon@me.com",
                     "agentDid": "did:sov:64",
                     "role": "SA"}
        },
        "signature": {
            "type": "ed25519-sha-256",
            "created": "2018-06-27T16:02:20Z", 
            "creator": "did:ixo:2p19P17cr6XavfMJ8htYSS",
            "signatureValue": "A011D11A2D91A9CB03ECFFB7D9AFC1001DB56B3DABF42BDD0F4D00352A9B8E0E73E85F0B4586DA2934696C0A78602EEB047EA6B3D9096C1A0C3FB144E6A51C09"
        }
    }
}
```

#### Create Entity

Creates a new entity.

Request:

```text
{
    "jsonrpc": "2.0", 
    "method": "createProject", 
    "id": 3, 
    "params": {
        "payload": {        
            "template": {
                "name": "<template to validate>"
            },
            "data": {
                <create project data>
            }
        },
        "signature": {
            "type": <signature type ECDSA or E25519>,
            "created": <date of signature>, 
            "creator": <user did>,
            "signatureValue":  <signature in hex>
        }
    }
}
```

Example:

```text
{
    "jsonrpc": "2.0",
    "method": "createProject",
    "id": 123,
    "params": {
        "payload": {
            "template": {
                "name": "create_project"
            },
            "data": {
                "title": "Water project",
                "ownerName": "Don",
                "ownerEmail": "don@gmail.com",
                "shortDescription": "Project for water",
                "longDescription": "project to save water for areas with drought",
                "impactAction": "litres of water saved",
                "projectLocation": "ZA",
                "sdgs": [
                  "12.2",
                  "3",
                  "2.4"
                ],
                "requiredClaims": 30,
                "templates": {
                  "claim": {
                    "schema": "af175axcn6ejiuds0sh",
                    "form": "1v6v8a6woabjiuds3i9"
                  }
                },
                "evaluatorPayPerClaim": "0",
                "socialMedia": {
                  "facebookLink": "https://www.facebook.com/ixofoundation/",
                  "instagramLink": "",
                  "twitterLink": "",
                  "webLink": "https://ixo.foundation"
                },
                "serviceEndpoint": "http://35.192.187.110:5000/",
                "imageLink": "pc16l7yk62ejiudrox5",
                "founder": {
                  "name": "Nic",
                  "email": "nic@test.co.za",
                  "countryOfOrigin": "ZA",
                  "shortDescription": "primary description for founder",
                  "websiteURL": "www.water.com",
                  "logoLink": ""
                }
            }
        },
         "signature": {
            "type": "ed25519-sha-256",
            "created": "2018-06-05T12:35:02Z", 
            "creator": "did:ixo:2p19P17cr6XavfMJ8htYSS",
            "signatureValue": "23EED2462B11B94C9F63A509B39F15CB9C0B2DB8C16A52A22115B755BF3F6BDF7ABB8881697AA7DB6F4AFBD7C5DE4618B403AB43B738841BB89E72C8792AC401"
        }
    }
}
```

Response:

```text
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": {
        "__v": 0,
        <project data>
        "tx": "b51cd2665d146d0a0240fd2756beb4c9e9c1948275ac5d37a7ae405ab2d71a7a",
        "_id": "5a66e09b38f45f01d90d122a",
    }
}
```

Example:

```text
{
    "jsonrpc": "2.0",
    "id": 123,
    "result": {
        "_id": "5b32094f05aa3f0011405957",
        "title": "Test Water project",
        "ownerName": "Don",
        "ownerEmail": "don@gmail.com",
        "shortDescription": "Project for water",
        "longDescription": "project to save water for areas with drought",
        "impactAction": "litres of water saved",
        "projectLocation": "ZA",
        "sdgs": [
            "12.2",
            "3",
            "2.4"
        ],
        "requiredClaims": 30,
        "templates": {
            "claim": {
                "schema": "af175axcn6ejiuds0sh",
                "form": "1v6v8a6woabjiuds3i9"
            }
        },
        "evaluatorPayPerClaim": "0",
        "socialMedia": {
            "facebookLink": "https://www.facebook.com/ixofoundation/",
            "instagramLink": "",
            "twitterLink": "",
            "webLink": "https://ixo.foundation"
        },
        "serviceEndpoint": "http://35.192.187.110:5000/",
        "imageLink": "pc16l7yk62ejiudrox5",
        "founder": {
            "name": "Nic",
            "email": "nic@test.co.za",
            "countryOfOrigin": "ZA",
            "shortDescription": "primary description for founder",
            "websiteURL": "www.water.com",
            "logoLink": ""
        },
        "txHash": "a09c8bc12a3e7cc1f859f0fc98cd37880d8c894826e0f1fa7a3f824db37941f5",
        "__v": 0
    }
}
```

#### Create Agent

Creates a new agent.

Request:

```text
{
    "jsonrpc": "2.0", 
    "method": "createAgent", 
    "id": 3, 
    "params": {
        "payload": {        
            "template": {
                "name": "<template to validate>"
            },
            "data": {
                <create agent data>
            }
        },
        "signature": {
            "type": <signature type ECDSA or E25519>,
            "created": <date of signature>, 
            "creator": <user did>,
            "signatureValue":  <signature in hex>
        }
    }
}
```

Response:

```text
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": {
        "__v": 0,
        <agent data>
        "tx": "b51cd2665d146d0a0240fd2756beb4c9e9c1948275ac5d37a7ae405ab2d71a7a",
        "_id": "5a66e09b38f45f01d90d122a",
        "version": 1
    }
}
```

#### Update Agent Status

Update Agent Status

Request:

```text
{
    "jsonrpc": "2.0", 
    "method": "updateAgentStatus", 
    "id": 3, 
    "params": {
        "payload": {        
            "template": {
                "name": "<template to validate>"
            },
            "data": {
                <update agent data>
            }
        },
        "signature": {
            "type": <signature type ECDSA or E25519>,
            "created": <date of signature>, 
            "creator": <user did>,
            "signatureValue":  <signature in hex>
        }
    }
}
```

Response:

```text
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": {
        "__v": 0,
        <agent data>
        "tx": "b51cd2665d146d0a0240fd2756beb4c9e9c1948275ac5d37a7ae405ab2d71a7a",
        "did": <creator's did>
        "_id": "5a66e09b38f45f01d90d122a",
        "version": 1
    }
}
```

#### List Agents

List claims and latest status.

Request:

```text
{
    "jsonrpc": "2.0", 
    "method": "listAgents", 
    "id": 3, 
    "params": {
        "payload": {        
            "template": {
                "name": "<template to validate>"
            },
            "data": {
                <data to filter>
            }
        },
        "signature": {
            "type": <signature type ECDSA or E25519>,
            "created": <date of signature>, 
            "creator": <user did>,
            "signatureValue":  <signature in hex>
        }
    }
}
```

Response:

```text
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": [
        {
            <agent data>,
            "currentStatus": {
                <agent status data>
            }
        }
    ]
}
```

#### Submit Claim

Creates a new claim.

Request:

```text
{
    "jsonrpc": "2.0", 
    "method": "submitClaim", 
    "id": 3, 
    "params": {
        "payload": {        
            "template": {
                "name": "<template to validate>"
            },
            "data": {
                <submit claim data>
            }
        },
        "signature": {
            "type": <signature type ECDSA or E25519>,
            "created": <date of signature>, 
            "creator": <user did>,
            "signatureValue":  <signature in hex>
        }
    }
}
```

Response:

```text
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": {
        "__v": 0,
        <claim data>
        "tx": "b51cd2665d146d0a0240fd2756beb4c9e9c1948275ac5d37a7ae405ab2d71a7a",
        "_id": "5a66e09b38f45f01d90d122a"
    }
}
```

#### Evaluate Claim

Evaluate a new claim.

Request:

```text
{
    "jsonrpc": "2.0", 
    "method": "evaluateClaim", 
    "id": 3, 
    "params": {
        "payload": {        
            "template": {
                "name": "<template to validate>"
            },
            "data": {
                <evaluate claim data>
            }
        },
        "signature": {
            "type": <signature type ECDSA or E25519>,
            "created": <date of signature>, 
            "creator": <user did>,
            "signatureValue":  <signature in hex>
        }
    }
}
```

Response:

```text
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": {
        "__v": 0,
        <claim data>
        "tx": "b51cd2665d146d0a0240fd2756beb4c9e9c1948275ac5d37a7ae405ab2d71a7a",
        "_id": "5a66e09b38f45f01d90d122a",
        "version": 1
    }
}
```

#### List Claim

List claims and latest status.

Request:

```text
{
    "jsonrpc": "2.0", 
    "method": "listClaims", 
    "id": 3, 
    "params": {
        "payload": {        
            "template": {
                "name": "<template to validate>"
            },
            "data": {
                <data to filter>
            }
        },
        "signature": {
            "type": <signature type ECDSA or E25519>,
            "created": <date of signature>, 
            "creator": <user did>,
            "signatureValue":  <signature in hex>
        }
    }
}
```

Response:

```text
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": [
        {
            <claim data>,
            "evaluations": {
                <claim status data>
            }
        }
    ]
}
```

#### List Claim by Template ID

List claims and latest status filtered by template ID. The template ID is expected to be included in `<data to filter>` as `claimTemplateId`.

Request:

```text
{
    "jsonrpc": "2.0", 
    "method": "listClaims", 
    "id": 3, 
    "params": {
        "payload": {        
            "template": {
                "name": "<template to validate>"
            },
            "data": {
                <data to filter>
            }
        },
        "signature": {
            "type": <signature type ECDSA or E25519>,
            "created": <date of signature>, 
            "creator": <user did>,
            "signatureValue":  <signature in hex>
        }
    }
}
```

Response:

```text
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": [
        {
            <claim data>,
            "evaluations": {
                <claim status data>
            }
        }
    ]
}
```

### Health Check Functions

#### Cell Node Health Check

URI: `<pds server>/`

Request type: `GET`

Response:

```text
API is running
```

The ixo-cellNode \(pds\) uses JSON-RPC to receive client requests. The structure of all calls follow the same structure:

## ixo Blockchain API

### DID Functions

#### Register DID Doc

Registers the DID Doc for the specified DID. The DID Doc must contain the DID and the public key which can be used to verify signatures signed by this DID.

Request:

|  |  |
| :--- | :--- |
| Server: | Blockchain TX Server |
| Method: | `GET` |
| URI: | `/broadcast_tx_sync?tx=` |
| Parameters: | _&lt;uppercase hex of the DID Doc with its signature preceded with Ox&gt;_ |

Example Request: `http://localhost:46657/broadcast_tx_sync?tx=0x7B227...355430383A34363A31372B30323030227D7D`

Example Parameter \(pre hex encoding\):

```text
{"payload":[{"type":"did/AddDid","value":{"didDoc":{"did":"Auw1mQ9UtdHUj88NAJFUu6","pubKey":"6QMiDUXvshwbjHhUmpv6GkRn7D1iuFms5mUoYvX6hpRT","credentials":[]}}}],"signatures":[{"signatureValue":"lpb8jlhZc4i7CU30MucZSEujrHEfKPwh6mrladE4Pus4Z5fr2vP2sDc3XF1IW8Rk+8jcXW67G9EA20NlKVRAAg==","created":"2018-10-24T12:38:23.020Z"}]}
```

Response:

```text
{
  "did": "did.ixo.EvBFmtyRaBuMNMnwjHNVgn",
  "pubKey": "8awT75ZgZttei45J52bcXC2q8isMRATLcdgbmx4FHyFf",
  "credentials": []
}
```

#### Add a Credential to a DID Doc

Adds a signed credential to the DID Doc for the specified DID. The Credential must be signed by the DID of the credential issuer. The credential issuer's DID must already be registered \(to perpetuate a web of trust\).

Request:

|  |  |
| :--- | :--- |
| Server: | Blockchain TX Server |
| Method: | `GET` |
| URI: | `/broadcast_tx_sync?tx=` |
| Parameters: | _&lt;uppercase hex of the Add Credential Message with its signature preceded with Ox&gt;_ |

Example Request: `http://localhost:46657/broadcast_tx_sync?tx=0x7B227...355430383A34363A31372B30323030227D7D`

Example Parameter \(pre hex encoding\):

```text
{"payload":[{"type":"did/AddCredential","value":{"credential":{"type":["Credential","ProofOfKYC"],"issuer":"CDpBVRcnWEdvdkWJvNsj3y","issued":"2018-10-24T12:38:23.045Z","claim":{"id":"U66E8fQMKQgdkicNCuWdMU","KYCValidated":true}}}}],"signatures":[{"signatureValue":"+70QwmONskyWdsSewdoIX6a52TZWDtY9+MLIjy0pHKww+HO6QeLdxPEZ1S6o9m5EjNJz+H6P7mWStx6dUx51DA==","created":"2018-10-24T12:38:23.052Z"}]}
```

Response:

```text
{
    jsonrpc: "2.0",
    id: "",
    result: {
        code: 0,
        data: "0116444848654657394731374D6342556B34357479374A6E012C3768446F346A724675713846727566666164595A6A7971374C39534E4536327765616E74534D7A466A78585801030102010A43726564656E7469616C010A50726F6F664F664B59430116444848654657394731374D6342556B34357479374A6E0119323031382D30372D31365431353A33393A34302B30323A30300116444848654657394731374D6342556B34357479374A6E010102010A43726564656E7469616C010A50726F6F664F664B59430116444848654657394731374D6342556B34357479374A6E0119323031382D30372D31365431353A35313A34342B30323A30300116444848654657394731374D6342556B34357479374A6E010102010A43726564656E7469616C010A50726F6F664F664B59430116444848654657394731374D6342556B34357479374A6E0119323031382D30372D31365431353A35313A34342B30323A30300116444848654657394731374D6342556B34357479374A6E01",
        log: "",
        hash: "91C033E74E27E7778BD0FE3481F82F839C92C5BC"
    }
}
```

#### Get DID Document

Returns the Document for the specified DID. This contains one or more public keys which can be used to verify signatures signed by this DID.

Request:

|  |  |
| :--- | :--- |
| Server: | Blockchain REST Server |
| Method: | `GET` |
| URI: | `/did` |
| Parameters: | _&lt;did&gt;_ |

Example: `http://localhost:1317/did/did.ixo.EvBFmtyRaBuMNMnwjHNVgn`

Response:

```text
{
  "did": "did.ixo.EvBFmtyRaBuMNMnwjHNVgn",
  "pubKey": "8awT75ZgZttei45J52bcXC2q8isMRATLcdgbmx4FHyFf",
  "credentials": [
    {   
        "credential":{
            "type": ["Credential","ProofOfKYC"],
            "issuer": "DHHeFW9G17McBUk45ty7Jn",
            "issued": "2018-07-16T15:51:44Z",
            "claim": {
                "id": "did.ixo.EvBFmtyRaBuMNMnwjHNVgn",
                "KYCValidated": true
            }
        }
    }
  ]
}
```

### Health Check Functions

#### Blockchain Health Check

Check whether a blockchain node is available.

Request:

|  |  |
| :--- | :--- |
| Server: | Blockchain TX Server |
| Method: | `GET` |
| URI: | `/heath` |

Example: `http://localhost:46657/health`

Response:

```text
{
jsonrpc: "2.0",
id: "",
result: { }
}
```

## ixo-blocksync Explorer API

Returns a the publicly available data pertaining to entities. May selectively be filtered on sync with the blockchain, to contain only entities associated with a Relayer Node.

### DID Functions

#### Get DID Doc

Returns the DID Document for the specified DID. This contains the public key which can be used to verify signatures signed by this DID.

Request:

|  |  |
| :--- | :--- |
| Server: | ixo Explorer |
| Method: | `GET` |
| URI: | `/api/did/getByDid/` |
| Parameters: | _&lt;did&gt;_ |

Example: `http://app.ixo.world:8080/api/did/getByDid/did.ixo.EvBFmtyRaBuMNMnwjHNVgn`

Response:

```text
{
  "did": "did.ixo.EvBFmtyRaBuMNMnwjHNVgn",
  "publicKey": "8awT75ZgZttei45J52bcXC2q8isMRATLcdgbmx4FHyFf",
  "credentials": [
    {   
        "credential":{
            "type": ["Credential","ProofOfKYC"],
            "issuer": "DHHeFW9G17McBUk45ty7Jn",
            "issued": "2018-07-16T15:51:44Z",
            "claim": {
                "id": "did.ixo.EvBFmtyRaBuMNMnwjHNVgn",
                "KYCValidated": true
            }
        }
    }
  ]
}
```

### Project Functions

#### List Projects

Lists all the projects

#### Get Project

Retrieves a project by project DID

#### Get Global Stats

Retrieves the global statistics and metrics for all projects

### Health Check Functions

#### Health Check

Check that the explorer node is available

