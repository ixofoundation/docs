# ixo BlockSync

## ixo-blocksync Explorer API

Returns a the publicly available data pertaining to entities. May selectively be filtered on sync with the blockchain, to contain only entities associated with a Relayer Node.

### DID Functions

#### Get DID Doc

Returns the DID Document for the specified DID. This contains the public key which can be used to verify signatures signed by this DID.

Request:

|             |                      |
| ----------- | -------------------- |
| Server:     | ixo Explorer         |
| Method:     | `GET`                |
| URI:        | `/api/did/getByDid/` |
| Parameters: | _\<did>_             |

Example: `http://app.ixo.world:8080/api/did/getByDid/did.ixo.EvBFmtyRaBuMNMnwjHNVgn`

Response:

```
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
