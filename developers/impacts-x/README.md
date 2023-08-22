# Adding ImpactsX Wallet to Your Site

This guide provides step-by-step instructions for integrating the ImpactsX wallet functionality into your website without using the [`@ixo/jambo-wallet-sdk`](https://www.npmjs.com/package/@ixo/jambo-wallet-sdk). By following this guide, you'll be able to connect to the wallet, retrieve keys, and sign transactions using the `impactsX` window object.

## Prerequisites

- You have a basic understanding of JavaScript and web development.
- Your website is whitelisted by Ixo for ImpactsX wallet access.

## Integration Steps

### 1. Connect to the ImpactsX Wallet

To start using the ImpactsX wallet, you need to connect to the desired blockchain network and validate your site against the whitelist. Use the `enable` method to achieve this:

```js
// Method signature: (chainNameOrId: string, chainNetwork?: ChainNetwork) => Promise<void>

// Option 1: Connect using the chainId
const chainId = 'ixo-5'; // The chain ID corresponding to the active app chain
await impactsX.enable(chainId);

// Option 2: Connect using the chainName and chainNetwork
const chainName = 'impacthub'; // The chain name from Cosmos chain registry
const chainNetwork = 'mainnet'; // or 'testnet', 'devnet'
await impactsX.enable(chainName, chainNetwork);
```

Please note:

- You can choose either the `chainId` or the combination of `chainName` and `chainNetwork` to connect.
- This step enables your site's connection to specific chain keys and signing but is currently limited to the current chain and chain network active in the app. If the site's chain doesn't match the app's, the connection will be rejected.
- This step also validates your site against the whitelist. It's crucial to call `impactsX.enable` before any other method, or the other methods will error out.
- The whitelist validation remains effective only while the site is present in the Impacts X app browser. Navigating away from the site, even briefly, will reset the permissions, requiring the site to call `impactsX.enable` again upon re-entry.

### 2. Retrieve Keys

You can retrieve keys associated with a specific chain (currently only the active chain in the app) using the `impactsX.getKey` method:

```js
const chainId = 'ixo-5'; // The chain ID you're connected to
const includeDid = true; // Set to true if you want to include DID information

const key = await impactsX.getKey(chainId, includeDid);

// key = {
//  name: string
//  algo: Algo
//  pubKey: string
//  address: string
//  bech32Address: string
//  isNanoLedger: boolean
//  isKeystone: boolean
//  did?: string
// }
```

Please note:

- If you expected `pubKey` and `address` to be of type Uint8Array, you're correct. The ImpactsX Wallet can only accept and return string values. Thus, the `address` and `pubKey` values in the returned key object are Uint8Array values encoded to strings using the `toHex` function from the `@cosmjs/encoding` package. To obtain the appropriate Uint8Array values, decode these values as follows:

```js
import { fromHex } from '@cosmjs/encoding';
// ...
const pubKey = fromHex(key.pubKey);
```

### 3. Create Offline Signer

To sign transactions, you'll need an offlineSigner. However, using the offlineSigner directly from the `impactsX` window object will cause unexpected errors. Similar to step 2, the methods inside offlineSigner can only accept and return strings. Thus, you'll need to create your own offline signer with the `impactsX.getAccounts` and the `impactsX.signDirect` methods and encode or decode the values where necessary.

```js
// Method signature: (chainId: string) => Promise<{ address: string; algo: Algo; pubkey: string; }[]>
import { fromHex } from '@cosmjs/encoding';

const chainId = 'ixo-5';

// create new `getAccounts` that decodes hex values to Uint8Array and removes chainId param
const getAccounts = async () => {
	const accounts = await impactsX.getAccounts(chainId);
	const decodedAccounts = accounts.map((account) => ({ ...account, pubKey: fromHex(account.pubkey) }));
	return decodedAccounts;
};
```

Please note:

- In the offlineSigner, the `getAccounts` methods require no chainId, whereas `impactsX.getAccounts` requires the chainId for it to function as needed. Hence, it's pre-generated and passed in when we recreate the getAccounts method.
- With `impactsX.getAccounts`, the pubkey is a hex-encoded Uint8Array value. All other values are correct, and only the pubkey must be decoded.

```js
// Method signature: (signerAddress: string, signDoc: { bodyBytes: string, authInfoBytes: string, chainId: string, accountNumber: string }): Promise<{ signed: { bodyBytes: string, authInfoBytes: string, chainId: string, accountNumber: string }, signature: { signature: string, pub_key: { type: string, value: any } } }>
import { toHex } from '@cosmjs/encoding';

// create new `signDirect` that encodes `Uint8Array` values from the params and decodes hex values to `Uint8Array` from the response
const signDirect = async (signerAddress, signDoc) => {
	const encodedSignDoc = {
		...signDoc,
		bodyBytes: toHex(signDoc.bodyBytes),
		authInfoBytes: toHex(signDoc.authInfoBytes),
		accountNumber: signDoc.accountNumber.toString(),
	};
	const response = await impactsX.signDirect(encodedSignDoc);
	const decodedResponse = {
		...response,
		signed: signDoc,
	};
	return decodedResponse;
};
```

Please note:

- The signDoc passed into `impactsX.signDirect` must have all its Uint8Array values encoded to hex strings via `@cosmjs/encoding`.
- The response from `impactsX.signDirect` will contain Uint8Array encoded values which should be decoded.
- The signing won't happen automatically; it requires user biometric authentication.

Now you can create your own offlineSigner with the getAccounts and signDirect functions you just created and pass this offlineSigner to the signing client to sign and broadcast transactions.

```js
const offlineSigner = { getAccounts, signDirect };

const client = await createSigningClient(chainRpcEndpoint, offlineSigner);

// sendTransaction(SigningClient, SignerAddress, { trx: msg[], chainId: string; fee: StdFee; memo?: string })
const result = await sendTransaction(client, address, payload);

console.log(result.hash); // Transaction hash
```

## Security

Impacts X will under no circumstances hand over a user's mnemonic or private keys, so there's no use in trying to extract them.

## Conclusion

By following these integration steps, you'll be able to seamlessly incorporate ImpactsX wallet functionality into your website. Feel free to use the [@ixo/jambo-wallet-sdk](https://www.npmjs.com/package/@ixo/jambo-wallet-sdk) for automatic encryption/decryption and easier integration.
