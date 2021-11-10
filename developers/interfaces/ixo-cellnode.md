# ixo CellNode

## Cell Node API

Note: the legacy name for Cell Node was Project Data Store (PDS).

A Cell Node is a decentralised data processing and storage node. This has a public API and private API. Public API requests do not require cryptographic signatures. All other requests must be signed and adhere to the capabilities that have been granted to the signer.

### Public API

URI: `<pds server>/api/public`

Request type: `POST`

Structure: `{"jsonrpc": "2.0", "method": "<method name>", "id": <message id>, "params": <json data object> }`

| Variable             | Description                                               |
| -------------------- | --------------------------------------------------------- |
| `<node server>`      | The URL of the server                                     |
| `<entity>`           | The entity to send the method                             |
| `<method name>`      | The name of the method to call defined in the config file |
| `<message id>`       | The message ID, used to correlate asynchronous responses  |
| `<json data object>` | The parameters that are passed to the method handler      |

#### Structure of the params object

These are unsigned requests for publicly available information. A content identifier is generated and sent back to the client, to be used in retrieval of this information.

Data will be accepted any of the following encodings: "ascii" | "utf8" | "utf16le" | "ucs2" | "base64" | "latin1" | "binary" | "hex".

contentType should reference a MIME type. See [https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics\_of\_HTTP/MIME\_types/Complete\_list\_of\_MIME\_types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics\_of\_HTTP/MIME\_types/Complete\_list\_of\_MIME\_types)

```
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

```
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

```
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": "<string>"
}
```

#### Fetch image

Request:

```
{
    "jsonrpc": "2.0", 
     "method": "fetchPublic", 
     "id": 3, 
     "params": {"key": <string>}
}
```

Response:

```
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

```
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

```
{
    "jsonrpc": "2.0",
    "id": 3,
    "result": "<string>"
}
```

#### Fetch Json file

Request:

```
{
    "jsonrpc": "2.0", 
     "method": "fetchPublic", 
     "id": 3, 
     "params": {"key": <string>}
}
```

Response:

```
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

| Variable             | Description                                               |
| -------------------- | --------------------------------------------------------- |
| `<node server>`      | The URL of the server                                     |
| `<entity>`           | The entity to send the method                             |
| `<method name>`      | The name of the method to call defined in the config file |
| `<message id>`       | The message ID, used to correlate asynchronous responses  |
| `<json data object>` | The parameters that are passed to the method handler      |

#### Structure of the params object

Everything in the payload section is signed to generate a valid signature. This should be packaged using `JSON.stringify()` method before signing.

```
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

```
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

```
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

```
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

```
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

```
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

```
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

```
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

```
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

```
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

```
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

```
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

```
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

```
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

```
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

```
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

```
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

```
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

```
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

```
API is running
```

The ixo-cellNode (pds) uses JSON-RPC to receive client requests. The structure of all calls follow the same structure:
