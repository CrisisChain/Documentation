# 🔐 Smart Contracts – CrisisChain Blockchain Aid Distribution

This document describes the smart contract logic and on-chain architecture for **CrisisChain**, a blockchain-powered aid distribution platform focused on transparency, traceability, and accountability.

---

## 📜 Overview

The CrisisChain smart contract system is designed to:

- ✅ Register and verify **aid beneficiaries**
- ✅ Mint and distribute **aid tokens**
- ✅ Log and track **transactions**
- ✅ Enforce rules on **claiming**, **expiration**, and **limits**

We currently use **Cardano/Midnight (for privacy support)** and write contracts in **Plutus (Haskell)** or **Aiken** (depending on the stack).

---

## 🏗 Contract Modules

### 1. `AidTokenContract`

Handles minting and distribution of aid tokens.

**Key Functions:**

- `mintAidToken(adminAddress, totalSupply)`
- `transferAidToken(toAddress, amount)`
- `burnAidToken(address, amount)`

**Events:**

- `AidTokenMinted`
- `AidTokenTransferred`
- `AidTokenBurned`

---

### 2. `BeneficiaryRegistryContract`

Verifies and registers intended aid recipients.

**Key Functions:**

- `registerBeneficiary(name, nationalId, walletAddress)`
- `verifyBeneficiary(walletAddress)`
- `banBeneficiary(walletAddress)`

**Events:**

- `BeneficiaryRegistered`
- `BeneficiaryVerified`
- `BeneficiaryBanned`

---

### 3. `AidClaimContract`

Controls the rules and conditions under which beneficiaries can claim aid.

**Key Functions:**

- `claimAid(walletAddress)`
- `setClaimLimit(amount)`
- `checkEligibility(walletAddress)`

**Rules:**

- Claim is only valid if:
  - The beneficiary is verified ✅
  - Tokens are available 💰
  - The beneficiary has not exceeded claim limits 📉

**Events:**

- `AidClaimed`
- `ClaimRejected`

---

### 4. `AuditLogContract` _(Optional)_

Tracks historical logs of token movements and interactions for transparency and external auditing.

**Functions:**

- `logTransaction(txHash, actionType, involvedAddresses)`
- `viewTransactionHistory(walletAddress)`

---

## 🛠 Technical Stack

| Layer           | Technology         |
| --------------- | ------------------ |
| Blockchain      | Cardano / Midnight |
| Smart Contracts | Plutus (or Aiken)  |
| Wallets         | Lace, Nami, Flint  |
| DApp Platform   | React + Supabase   |

---

## 🔐 Privacy Considerations (Midnight Network)

When using Midnight:

- Beneficiary identity can be protected via **zero-knowledge credentials**
- Token claim logs are **selectively transparent**
- Designed for compliance + security in sensitive zones

---

## 🧪 Testing & Simulation

Before deploying to mainnet:

- ✅ Use testnet wallets (Lace, Flint, Nami)
- ✅ Simulate token claims and transfers with fake UTXOs
- ✅ Validate smart contract logic with unit and property tests

---

## 📦 Deployment Checklist

- [ ] Audit contracts
- [ ] Test on testnet (Preview or Midnight)
- [ ] Deploy using CLI or Vercel GitHub Actions
- [ ] Connect with off-chain logic via wallet adapters

---

## 👥 Contributors

- Dibora Shibeshi – Project Lead
- Leyuthega Abebaw – Blockchain Developer
- Hana Tamiru – Integration Engineer

---

## 📬 Contact

📧 diborashibeshi@gmail.com  
🌐 GitHub: [github.com/Dibora12](https://github.com/Dibora12)

---
