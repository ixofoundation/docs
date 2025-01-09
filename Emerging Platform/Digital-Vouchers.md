---
stoplight-id: 13nf6kqrtl4ur
---

# Digital Vouchers

This guide details how to implement a Digital Voucher scheme in the Emerging Platform, leveraging IXO’s decentralized digital MRV (dMRV) and blockchain infrastructure. The scheme allows end-users (households adopting modern cooking solutions) to receive vouchers as an economic benefit share from the sale of Internationally Transferred Mitigation Outcomes (ITMOs). These vouchers can be redeemed for products and services with high Sustainable Development Goal (SDG) impact—ensuring users benefit directly from emissions trading revenue without hidden fees or intermediaries.

## Overview

1. **ITMO Generation**  
   - A Mitigation Activity issues ITMOs after verified emission reductions are recognized under Article 6 of the Paris Agreement.  
   - For each ITMO sold, part of the revenue is earmarked for end-user incentives.

2. **Voucher Creation**  
   - The system mints a unique digital voucher linked to a user’s decentralized identifier (DID).  
   - Each voucher has an on-chain representation as a token that specifies its value and redemption terms.

3. **Distribution to End-Users**  
   - Users are notified via a mobile app, SMS, or another interface that a voucher is available.  
   - The voucher is assigned to the user’s DID-based wallet or account, ensuring cryptographic ownership.

4. **Redemption**  
   - Users can redeem vouchers for selected goods and services (e.g., further cooking devices, fuel supplies, educational or healthcare benefits) from partner suppliers.  
   - Once redeemed, the voucher is marked as spent or burned, preventing double usage.

5. **Settlements & Reporting**  
   - Merchants or service providers receive payment or credit in exchange for accepting vouchers.  
   - The Emerging Platform tracks each step, ensuring transparency and full value transfer to end-users.
## Key Technical Components

### Decentralized Identifiers (DIDs)
- **User DID**: Each end-user (household or individual) holds a unique DID, used to receive and hold vouchers.  
- **Merchant DID**: Partner merchants or service providers also have DIDs, enabling them to verify voucher authenticity and redeem them on the platform.  
- **Project DID**: The project or organization issuing the vouchers may have a DID that signs voucher contracts or conditions.

### Verifiable Credentials & Tokens
- **Voucher Credential**: A cryptographic document binding the voucher’s value, expiration date, and redemption conditions to the user’s DID.  
- **On-Chain Representation**: Vouchers are minted as digital tokens

### 2.3 Smart Contracts
- **Minting Contract**: Issues new vouchers when ITMOs are sold, ensuring a transparent link between ITMO revenue and voucher creation.  
- **Redemption Contract**: Tracks voucher usage, verifying that a user meets redemption conditions and preventing double-spending.  
- **Settlement Contract**: Handles merchant reimbursements, ensuring they receive the promised value once a voucher is redeemed.

### Oracle Services
- **ITMO Sales Data**: Oracles confirm that an ITMO transaction occurred on the carbon registry or marketplace.  
- **Voucher Trigger**: After verifying ITMO revenue, the Oracle triggers the minting contract to create a corresponding voucher.  
- **Redemption Verification**: Oracles can validate that a user actually redeemed a voucher under the specified conditions (e.g., a user physically collected goods at a merchant location).

## Voucher Creation & Distribution

### Linking Vouchers to ITMO Sales
1. **ITMO Sale Event**  
   - When a transaction on an ITMO marketplace completes, the platform logs the revenue details.  
2. **Oracle Notification**  
   - The Oracle checks the sale data for accuracy, including the quantity of ITMOs and final price.  
3. **Minting Contract**  
   - The Oracle calls the Minting Contract, specifying the user’s DID, the voucher’s numeric value, and relevant metadata (e.g., voucher ID, issuance date, expiry date).

#### Example Pseudocode
```pseudo
function onITMOSale( saleDetails ):
    if saleDetails.isValid():
        voucherValue = calculateVoucherValue(saleDetails)
        mintVoucher({
          userDid: saleDetails.recipient,
          value: voucherValue,
          issuanceDate: now(),
          expirationDate: now() + 180 days
        })
```

### Voucher Metadata
Each voucher includes:
- **Unique ID**: For tracking and reference in smart contracts.  
- **Value**: Monetary amount, credit points, or other measure.  
- **Expiration**: A date/time by which the voucher must be redeemed.  
- **Conditions**: Specific terms (e.g., “valid only for certain products,” “no cash exchange”).  
- **Proofs**: Cryptographic signatures from the voucher issuer.

### Notification Mechanisms
- **Mobile App**: A push notification containing voucher details.  
- **SMS**: Short message with voucher code for low-connectivity regions.  
- **Web Portal**: Users can log into their DID-based dashboard to see available vouchers.

## Redemption Workflow

### Checking Eligibility
- A merchant’s point-of-sale (POS) or a web interface queries the user’s DID for valid, unspent vouchers.  
- The user presents a credential or token proving voucher ownership.

### Merchant Confirmation
1. **Voucher Validation**  
   - The merchant’s system checks the voucher’s metadata, cryptographic signatures, and expiry.  
   - Ensures the voucher has not already been redeemed or voided.
2. **Authorization**  
   - If valid, the merchant’s system requests redemption from the Redemption Contract.

#### Example REST Call
```http
POST /v1/vouchers/redeem
{
  "voucherId": "VCHR-XYZ-1234",
  "redeemerDid": "did:ixo:entity:user",
  "merchantDid": "did:ixo:entity:merchant"
}
```

### Smart Contract Execution
- **Redemption Contract** updates the voucher’s state (from “active” to “redeemed”).  
- **Emit Event**: A redemption event is recorded on the blockchain.  
- **Settlement Trigger**: If relevant, a settlement function can release funds or credit to the merchant.

### Proof of Redemption
- An on-chain log or transaction receipt indicates the voucher is spent.  
- The user’s DID wallet no longer lists that voucher as “available.”

## Settlement with Merchants

### Merchant Payout
1. **Settlement Contract**: Upon voucher redemption, calls a function to credit the merchant.  
2. **Payment Method**: Could be stablecoins, a local currency bank transfer, or an off-chain arrangement logged for transparency.  
3. **Reconciliation**: Transaction details feed into project analytics and financial systems for periodic auditing.

#### Example Pseudocode
```pseudo
function redeemVoucher(voucherId, redeemerDid, merchantDid):
    require(isVoucherUnspent(voucherId) == true)
    markVoucherRedeemed(voucherId, merchantDid, now())
    settlementAmount = getVoucherValue(voucherId)
    payMerchant(merchantDid, settlementAmount)
```

### Reporting & Audit Trails
- **On-Chain Ledger**: Each redemption triggers a cryptographically verifiable record, ensuring no double redemption or hidden fees.  
- **Off-Chain Reconciliation**: Merchants or project developers can export transaction logs for accounting or regulatory compliance.

## Security & Trust Mechanisms

### DID & Credential Security
- Each user has a private key controlling their DID. Only they can authorize voucher transfers or redemptions.  
- Vouchers are signed by the project issuer, preventing unauthorized creation or alteration.

### Anti-Fraud & Double-Spend Prevention
- The voucher state transitions from “active” to “redeemed” on the blockchain, making duplication or reuse impossible.  
- Cryptographic proofs and real-time contract checks ensure only valid vouchers can be spent.

### Privacy Considerations
- Voucher metadata can omit personal user info, referencing only the user’s DID.  
- Off-chain storage of personal data may be used if needed for KYC/AML requirements or to comply with local regulations.

## Technical Integration Steps for Developers

Below is a step-by-step outline for developers integrating the voucher scheme into their apps or services:

1. **Deploy Smart Contracts**  
   - Minting Contract: Handles voucher issuance post-ITMO sale.  
   - Redemption/Settlement Contract: Manages redemption requests and merchant payouts.

2. **Register Entities (DIDs)**  
   - Each user, merchant, and the project itself must have a DID.  
   - Store DID documents on the Emerging Platform’s DID registry for easy lookup and trust verification.

3. **Develop or Integrate a Wallet**  
   - Provide a user-friendly interface where end-users can see voucher balances, transaction history, and redeem vouchers.  
   - The same wallet could store carbon credits, credentials, or other digital assets.

4. **Implement Oracle Functionality**  
   - Oracle for ITMO Sales: Observes external carbon marketplaces, triggers voucher minting.  
   - Oracle for Redemption: (Optional) Validates offline redemption claims or cross-checks external data sources.

5. **Merchant Integration**  
   - Expose APIs or a web dashboard for merchants to scan user credentials and trigger redemptions.  
   - Provide instructions on how to handle refunds, partial redemptions, or expansions of accepted voucher types.

6. **Notification System**  
   - Implement push notifications, SMS, or email to inform users when new vouchers are issued.  
   - Notify merchants of successful redemptions and any relevant settlement details.

7. **Monitoring & Analytics**  
   - Track voucher distribution, redemption rates, merchant payment flows, and potential fraud signals.  
   - Generate reports for stakeholders or auditors, showing how ITMO revenue is disbursed to end-users.

## Example User Journey

1. **Emission Reductions Verified**  
   A household using modern cooking solutions generates verified emission reductions. The project obtains an ITMO for this carbon credit.
2. **ITMO Sale**  
   An international buyer purchases the ITMO from the project’s marketplace listing.
3. **Voucher Minting**  
   Once the sale is confirmed, the Oracle triggers the minting contract to create a digital voucher worth USD 10 (for example).
4. **User Notification**  
   The user receives a message: “You have a new voucher valued at USD 10, redeemable at Partner Merchants until December 31.”
5. **Redemption**  
   The user presents the voucher credential at a partner store for a product or service. The store’s system verifies the voucher is legitimate, then redeems it.
6. **Settlement**  
   The merchant receives a payment or token credit from the project’s settlement contract.  
7. **Audit & Reporting**  
   The entire flow is recorded on the blockchain, providing an auditable trail demonstrating that end-users fully benefited from the ITMO proceeds.

## Best Practices and Recommendations

1. **Scalability**  
   - Use layer-2 solutions or sidechains for high-volume voucher issuance if transaction fees on the main chain are too high.  
   - Cache voucher states for quick lookups.

2. **User Experience (UX)**  
   - Provide simple redemption flows (e.g., scanning a QR code or tapping a mobile app button).  
   - Offer clear instructions in local languages, especially for end-users unfamiliar with blockchain.

3. **Security & Privacy**  
   - Encrypt sensitive data off-chain.  
   - Deploy robust authentication for merchant dashboards.  
   - Implement role-based access for administrators.

4. **Compliance**  
   - Stay up-to-date with local financial regulations (e.g., e-money, voucher laws).  
   - Implement KYC/AML checks if required for large-value vouchers or cross-border payments.

5. **Flexible Redemption Options**  
   - Partner with a diverse set of merchants (health, education, cooking fuel, etc.) to maximize SDG impact.  
   - Create partial redemption or top-up features so users can combine vouchers for higher-value products.

## Conclusion

By integrating a digital voucher scheme into the Emerging Platform, project developers ensure that revenue from ITMO sales directly benefits end-users who adopt modern cooking solutions. This closed-loop system delivers maximum transparency, prevents misappropriation, and demonstrates tangible SDG impact to funders and stakeholders. From minting vouchers linked to ITMO sales, to redemption and merchant settlement, the entire process leverages decentralized identifiers, verifiable credentials, and smart contracts to enable a secure and frictionless experience.

A successful implementation will not only enhance user engagement and trust but also differentiate the project by showcasing how carbon finance can be directly channeled to local communities. Through the use of cryptographic proofs, blockchain-based record-keeping, and user-friendly integration strategies, developers can build a robust, future-proof platform that merges climate action with genuine social and economic benefits.
