---
description: API Access Calls to the IXO Block Sync
---

# API's

#### In order to integrate, 

#### BasePath: block\_sync\_pandora.ixo.world

### Access

### Methods

#### Table of Contents

**Dids**

* `get /api/did/getByDid/:did`

**Projects**

* `get /getByProjectDid/:projectDid`
* `get /getProjectAccounts/:projectDid`
* `get /listProjects`

**Stats**

* `get /api/stats/listStats`

**Transaction**

* `get /api/blockchain/:tx`

## Dids

```text
get /api/did/getByDid/:did
```

Returns the did document for a specific did

#### Path parameters

did \(required\)

#### Responses

**200**

 did document DidDoc

#### Example data

Content-Type: application/json

```text
{
  "credentials" : [ {
    "claim" : {
      "id" : "id",
      "KYCValidated" : true
    },
    "type" : [ "type", "type" ],
    "issuer" : "issuer"
  }, {
    "claim" : {
      "id" : "id",
      "KYCValidated" : true
    },
    "type" : [ "type", "type" ],
    "issuer" : "issuer"
  } ],
  "publicKey" : "publicKey",
  "did" : "did"
}
```



## Projects

### Get by project Did

```text
get /getByProjectDid/:projectDid
```

Returns a list of projects belonging to a project did

#### Path parameters

projectDid \(required\)

Path Parameter — Project did

#### Responses

**200**

 List of Projects Projects

#### Example data

Content-Type: application/json

```text
{
  "projects" : [ {
    "senderDid" : "senderDid",
    "projectDid" : "projectDid",
    "data" : {
      "longDescription" : "longDescription",
      "projectLocation" : "projectLocation",
      "ixo" : {
        "totalUsed" : 1.024645700144157789424070870154537260532379150390625,
        "totalStaked" : 1.231513536777255612975068288506008684635162353515625
      },
      "founder" : {
        "logoLink" : "logoLink",
        "websiteURL" : "websiteURL",
        "name" : "name",
        "countryOfOrigin" : "countryOfOrigin",
        "shortDescription" : "shortDescription",
        "email" : "email"
      },
      "templates" : {
        "claim" : {
          "schema" : "schema",
          "form" : "form"
        }
      },
      "sdgs" : [ 6.02745618307040320615897144307382404804229736328125, 6.02745618307040320615897144307382404804229736328125 ],
      "shortDescription" : "shortDescription",
      "serviceEndpoint" : "serviceEndpoint",
      "title" : "title",
      "socialMedia" : {
        "instagramLink" : "instagramLink",
        "webLink" : "webLink",
        "twitterLink" : "twitterLink",
        "facebookLink" : "facebookLink"
      },
      "createdOn" : "createdOn",
      "requiredClaims" : 0.80082819046101150206595775671303272247314453125,
      "claimStats" : {
        "currentSuccessful" : 1.46581298050294517310021547018550336360931396484375,
        "currentRejected" : 5.962133916683182377482808078639209270477294921875
      },
      "ownerEmail" : "ownerEmail",
      "agents" : {
        "investorsPending" : 7.3862819483858839220147274318151175975799560546875,
        "evaluators" : 7.061401241503109105224211816675961017608642578125,
        "evaluatorsPending" : 9.301444243932575517419536481611430644989013671875,
        "serviceProviders" : 3.61607674925191080461672754609026014804840087890625,
        "serviceProvidersPending" : 2.027123023002321833274663731572218239307403564453125,
        "investors" : 4.1456080298839363962315474054776132106781005859375
      },
      "imageLink" : "imageLink",
      "ownerName" : "ownerName",
      "impactAction" : "impactAction",
      "bondId" : "bondId",
      "nodeId" : "nodeId",
      "createdBy" : "createdBy",
      "claims" : [ {
        "date" : "date",
        "saDid" : "saDid",
        "location" : {
          "long" : 5.63737665663332876420099637471139430999755859375,
          "lat" : 2.3021358869347654518833223846741020679473876953125
        },
        "claimId" : "claimId",
        "status" : "status",
        "eaDid" : "eaDid"
      }, {
        "date" : "date",
        "saDid" : "saDid",
        "location" : {
          "long" : 5.63737665663332876420099637471139430999755859375,
          "lat" : 2.3021358869347654518833223846741020679473876953125
        },
        "claimId" : "claimId",
        "status" : "status",
        "eaDid" : "eaDid"
      } ]
    },
    "txHash" : "txHash",
    "pubKey" : "pubKey",
    "status" : "status"
  }, {
    "senderDid" : "senderDid",
    "projectDid" : "projectDid",
    "data" : {
      "longDescription" : "longDescription",
      "projectLocation" : "projectLocation",
      "ixo" : {
        "totalUsed" : 1.024645700144157789424070870154537260532379150390625,
        "totalStaked" : 1.231513536777255612975068288506008684635162353515625
      },
      "founder" : {
        "logoLink" : "logoLink",
        "websiteURL" : "websiteURL",
        "name" : "name",
        "countryOfOrigin" : "countryOfOrigin",
        "shortDescription" : "shortDescription",
        "email" : "email"
      },
      "templates" : {
        "claim" : {
          "schema" : "schema",
          "form" : "form"
        }
      },
      "sdgs" : [ 6.02745618307040320615897144307382404804229736328125, 6.02745618307040320615897144307382404804229736328125 ],
      "shortDescription" : "shortDescription",
      "serviceEndpoint" : "serviceEndpoint",
      "title" : "title",
      "socialMedia" : {
        "instagramLink" : "instagramLink",
        "webLink" : "webLink",
        "twitterLink" : "twitterLink",
        "facebookLink" : "facebookLink"
      },
      "createdOn" : "createdOn",
      "requiredClaims" : 0.80082819046101150206595775671303272247314453125,
      "claimStats" : {
        "currentSuccessful" : 1.46581298050294517310021547018550336360931396484375,
        "currentRejected" : 5.962133916683182377482808078639209270477294921875
      },
      "ownerEmail" : "ownerEmail",
      "agents" : {
        "investorsPending" : 7.3862819483858839220147274318151175975799560546875,
        "evaluators" : 7.061401241503109105224211816675961017608642578125,
        "evaluatorsPending" : 9.301444243932575517419536481611430644989013671875,
        "serviceProviders" : 3.61607674925191080461672754609026014804840087890625,
        "serviceProvidersPending" : 2.027123023002321833274663731572218239307403564453125,
        "investors" : 4.1456080298839363962315474054776132106781005859375
      },
      "imageLink" : "imageLink",
      "ownerName" : "ownerName",
      "impactAction" : "impactAction",
      "bondId" : "bondId",
      "nodeId" : "nodeId",
      "createdBy" : "createdBy",
      "claims" : [ {
        "date" : "date",
        "saDid" : "saDid",
        "location" : {
          "long" : 5.63737665663332876420099637471139430999755859375,
          "lat" : 2.3021358869347654518833223846741020679473876953125
        },
        "claimId" : "claimId",
        "status" : "status",
        "eaDid" : "eaDid"
      }, {
        "date" : "date",
        "saDid" : "saDid",
        "location" : {
          "long" : 5.63737665663332876420099637471139430999755859375,
          "lat" : 2.3021358869347654518833223846741020679473876953125
        },
        "claimId" : "claimId",
        "status" : "status",
        "eaDid" : "eaDid"
      } ]
    },
    "txHash" : "txHash",
    "pubKey" : "pubKey",
    "status" : "status"
  } ]
}
```

### Get Project Accounts

```text
get /getProjectAccounts/:projectDid
```

Returns a list of accounts belonging to a project

#### Path parameters

projectDid \(required\)

#### Responses

**200**

 List of Accounts

#### Example data

Content-Type: application/json

```text
{
  "accounts" : [ {
    "sequence" : "sequence",
    "address" : "address",
    "coins" : {
      "accounts" : [ {
        "amount" : 0.80082819046101150206595775671303272247314453125,
        "denom" : "denom"
      }, {
        "amount" : 0.80082819046101150206595775671303272247314453125,
        "denom" : "denom"
      } ]
    },
    "name" : "name",
    "accountNumber" : "accountNumber",
    "pubKey" : "pubKey"
  }, {
    "sequence" : "sequence",
    "address" : "address",
    "coins" : {
      "accounts" : [ {
        "amount" : 0.80082819046101150206595775671303272247314453125,
        "denom" : "denom"
      }, {
        "amount" : 0.80082819046101150206595775671303272247314453125,
        "denom" : "denom"
      } ]
    },
    "name" : "name",
    "accountNumber" : "accountNumber",
    "pubKey" : "pubKey"
  } ]
}
```

#### 

##  List Projects

Returns a list of projects

#### Responses

**200**

 List of Projects

#### Example data

Content-Type: application/json

```text
{
  "projects" : [ {
    "senderDid" : "senderDid",
    "projectDid" : "projectDid",
    "data" : {
      "longDescription" : "longDescription",
      "projectLocation" : "projectLocation",
      "ixo" : {
        "totalUsed" : 1.024645700144157789424070870154537260532379150390625,
        "totalStaked" : 1.231513536777255612975068288506008684635162353515625
      },
      "founder" : {
        "logoLink" : "logoLink",
        "websiteURL" : "websiteURL",
        "name" : "name",
        "countryOfOrigin" : "countryOfOrigin",
        "shortDescription" : "shortDescription",
        "email" : "email"
      },
      "templates" : {
        "claim" : {
          "schema" : "schema",
          "form" : "form"
        }
      },
      "sdgs" : [ 6.02745618307040320615897144307382404804229736328125, 6.02745618307040320615897144307382404804229736328125 ],
      "shortDescription" : "shortDescription",
      "serviceEndpoint" : "serviceEndpoint",
      "title" : "title",
      "socialMedia" : {
        "instagramLink" : "instagramLink",
        "webLink" : "webLink",
        "twitterLink" : "twitterLink",
        "facebookLink" : "facebookLink"
      },
      "createdOn" : "createdOn",
      "requiredClaims" : 0.80082819046101150206595775671303272247314453125,
      "claimStats" : {
        "currentSuccessful" : 1.46581298050294517310021547018550336360931396484375,
        "currentRejected" : 5.962133916683182377482808078639209270477294921875
      },
      "ownerEmail" : "ownerEmail",
      "agents" : {
        "investorsPending" : 7.3862819483858839220147274318151175975799560546875,
        "evaluators" : 7.061401241503109105224211816675961017608642578125,
        "evaluatorsPending" : 9.301444243932575517419536481611430644989013671875,
        "serviceProviders" : 3.61607674925191080461672754609026014804840087890625,
        "serviceProvidersPending" : 2.027123023002321833274663731572218239307403564453125,
        "investors" : 4.1456080298839363962315474054776132106781005859375
      },
      "imageLink" : "imageLink",
      "ownerName" : "ownerName",
      "impactAction" : "impactAction",
      "bondId" : "bondId",
      "createdBy" : "createdBy",
      "claims" : [ {
        "date" : "date",
        "saDid" : "saDid",
        "location" : {
          "long" : 5.63737665663332876420099637471139430999755859375,
          "lat" : 2.3021358869347654518833223846741020679473876953125
        },
        "claimId" : "claimId",
        "status" : "status",
        "eaDid" : "eaDid"
      }, {
        "date" : "date",
        "saDid" : "saDid",
        "location" : {
          "long" : 5.63737665663332876420099637471139430999755859375,
          "lat" : 2.3021358869347654518833223846741020679473876953125
        },
        "claimId" : "claimId",
        "status" : "status",
        "eaDid" : "eaDid"
      } ]
    },
    "txHash" : "txHash",
    "pubKey" : "pubKey",
    "status" : "status"
  }, {
    "senderDid" : "senderDid",
    "projectDid" : "projectDid",
    "data" : {
      "longDescription" : "longDescription",
      "projectLocation" : "projectLocation",
      "ixo" : {
        "totalUsed" : 1.024645700144157789424070870154537260532379150390625,
        "totalStaked" : 1.231513536777255612975068288506008684635162353515625
      },
      "founder" : {
        "logoLink" : "logoLink",
        "websiteURL" : "websiteURL",
        "name" : "name",
        "countryOfOrigin" : "countryOfOrigin",
        "shortDescription" : "shortDescription",
        "email" : "email"
      },
      "templates" : {
        "claim" : {
          "schema" : "schema",
          "form" : "form"
        }
      },
      "sdgs" : [ 6.02745618307040320615897144307382404804229736328125, 6.02745618307040320615897144307382404804229736328125 ],
      "shortDescription" : "shortDescription",
      "serviceEndpoint" : "serviceEndpoint",
      "title" : "title",
      "socialMedia" : {
        "instagramLink" : "instagramLink",
        "webLink" : "webLink",
        "twitterLink" : "twitterLink",
        "facebookLink" : "facebookLink"
      },
      "createdOn" : "createdOn",
      "requiredClaims" : 0.80082819046101150206595775671303272247314453125,
      "claimStats" : {
        "currentSuccessful" : 1.46581298050294517310021547018550336360931396484375,
        "currentRejected" : 5.962133916683182377482808078639209270477294921875
      },
      "ownerEmail" : "ownerEmail",
      "agents" : {
        "investorsPending" : 7.3862819483858839220147274318151175975799560546875,
        "evaluators" : 7.061401241503109105224211816675961017608642578125,
        "evaluatorsPending" : 9.301444243932575517419536481611430644989013671875,
        "serviceProviders" : 3.61607674925191080461672754609026014804840087890625,
        "serviceProvidersPending" : 2.027123023002321833274663731572218239307403564453125,
        "investors" : 4.1456080298839363962315474054776132106781005859375
      },
      "imageLink" : "imageLink",
      "ownerName" : "ownerName",
      "impactAction" : "impactAction",
      "bondId" : "bondId",
      "createdBy" : "createdBy",
      "claims" : [ {
        "date" : "date",
        "saDid" : "saDid",
        "location" : {
          "long" : 5.63737665663332876420099637471139430999755859375,
          "lat" : 2.3021358869347654518833223846741020679473876953125
        },
        "claimId" : "claimId",
        "status" : "status",
        "eaDid" : "eaDid"
      }, {
        "date" : "date",
        "saDid" : "saDid",
        "location" : {
          "long" : 5.63737665663332876420099637471139430999755859375,
          "lat" : 2.3021358869347654518833223846741020679473876953125
        },
        "claimId" : "claimId",
        "status" : "status",
        "eaDid" : "eaDid"
      } ]
    },
    "txHash" : "txHash",
    "pubKey" : "pubKey",
    "status" : "status"
  } ]
}
```

#### 

## Stats

###  Get Stats

```text
get /api/stats/listStats
```



Returns the statistics for projects

#### Path parameters

tx \(required\)

#### Responses

**200**

 stats result 

#### Example data

Content-Type: application/json

```text
{
  "total" : 0.80082819046101150206595775671303272247314453125,
  "totalSuccessful" : 6.02745618307040320615897144307382404804229736328125,
  "totalPending" : 5.962133916683182377482808078639209270477294921875,
  "claimLocations" : [ {
    "long" : 5.63737665663332876420099637471139430999755859375,
    "lat" : 2.3021358869347654518833223846741020679473876953125
  }, {
    "long" : 5.63737665663332876420099637471139430999755859375,
    "lat" : 2.3021358869347654518833223846741020679473876953125
  } ],
  "totalSubmitted" : 1.46581298050294517310021547018550336360931396484375,
  "totalRejected" : 5.63737665663332876420099637471139430999755859375
}
```

## Transaction

### sendTransaction 

```text
get /api/blockchain/:tx
```

Forwards a transaction to the ixo-node for validation

#### Responses

**200**

 response object from ixo-node TxResponse

#### Example data

Content-Type: application/json

```text
{
  "result" : {
    "code" : 0.80082819046101150206595775671303272247314453125,
    "data" : "data",
    "log" : "log",
    "hash" : "hash"
  },
  "id" : "id",
  "jsonrpc" : "jsonrpc",
  "error" : {
    "code" : 6.02745618307040320615897144307382404804229736328125,
    "data" : "data",
    "message" : "message"
  }
}
```

#### 

### Models

#### `Account`

name \(optional\)

accountNumber \(optional\)

address \(optional\)

coins \(optional\)

pubKey \(optional\)

sequence \(optional\)

#### `Agents`

evaluators \(optional\)

evaluatorsPending \(optional\)

serviceProviders \(optional\)

serviceProvidersPending \(optional\)

investors \(optional\)

investorsPending \(optional\)

#### `Claim`

date \(optional\)

location \(optional\)

claimId \(optional\)

status \(optional\)

saDid \(optional\)

eaDid \(optional\)

#### `ClaimStats`

currentSuccessful \(optional\)

currentRejected \(optional\)

#### `Coin`

denom \(optional\)

amount \(optional\)

#### `DidDoc`

did \(optional\)

publicKey \(optional\)

credentials \(optional\)

#### `Founder`

name \(optional\)

email \(optional\)

countryOfOrigin \(optional\)

shortDescription \(optional\)

websiteURL \(optional\)

logoLink \(optional\)

#### `Ixo`

totalStaked \(optional\)

totalUsed \(optional\)

#### `Project`

data \(optional\)

projectDid \(optional\)

pubKey \(optional\)

senderDid \(optional\)

txHash \(optional\)

status \(optional\)

#### `ProjectData`

title \(optional\)

ownerName \(optional\)

ownerEmail \(optional\)

shortDescription \(optional\)

longDescription \(optional\)

impactAction \(optional\)

createdOn \(optional\)

createdBy \(optional\)

bondId \(optional\)

nodeId \(optional\)

projectLocation \(optional\)

requiredClaims \(optional\)

sdgs \(optional\)

claimStats \(optional\)

claims \(optional\)

templates \(optional\)

agents \(optional\)

socialMedia \(optional\)

ixo \(optional\)

serviceEndpoint \(optional\)

imageLink \(optional\)

founder \(optional\)

#### `SocialMedia`

facebookLink \(optional\)

instagramLink \(optional\)

twitterLink \(optional\)

webLink \(optional\)

#### `Stats`

total \(optional\)

totalSuccessful \(optional\)

totalSubmitted \(optional\)

totalPending \(optional\)

totalRejected \(optional\)

claimLocations \(optional\)

#### `TxError`

code \(optional\)

message \(optional\)

data \(optional\)

#### `TxResponse`

jsonrpc \(optional\)

id \(optional\)

result \(optional\)

error \(optional\)

#### `TxResult`

code \(optional\)

data \(optional\)

log \(optional\)

hash \(optional\)

