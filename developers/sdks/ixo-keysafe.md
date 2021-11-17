# ixo KeySafe

## Keysafe Browser Extension API

[GitHub ixo-keysafe repo](https://github.com/ixofoundation/ixo-keysafe)

When the keysafe extension operates through the browser `window` object.\
This can be accessed as follows:

```
const IxoInpageProvider = window['ixoKs'];
let keysafe = new IxoInpageProvider();
```

### Information Functions

#### Get User Information

Returns a javascript object containing a user name and associated DID Document from the keysafe local store.

Request:

```
keysafe.getInfo().then((error, result) => {
    if (result) {
        console.log('User Info: ' + result)
    } else {
        console.log(error)
    }
})
```

Response:

```
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

```
keysafe.getDidDoc().then((error, result) => {
    if (result) {
        console.log('User DID Doc: ' + result)
    } else {
        console.log(error)
    }
})
```

Response:

```
{
  "did": "did:ixo:2HQrdvfjqZwRQCapLDPZzY",
  "pubKey": "hZHiC5kPgiADRXnuiktvmsNSPH1D4c96NxMSjjNLVTY",
}
```

### Signing Functions

#### Request Signing

Request the user to sign some data using their keys in the keysafe wallet.

```
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
