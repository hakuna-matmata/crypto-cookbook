# How Crypto Works: Wallets, Transactions & Custody

**Reading Time:** ~25 minutes
**Audience:** Beginners ready for practical knowledge
**Level:** Beginner
**Updated:** January 2026

---

## What You'll Learn

This document explains the practical side of crypto:
- How wallets actually work (they don't "hold" your crypto)
- How transactions move from your device to the blockchain
- Different custody models and their trade-offs
- How to stay secure

By the end, you'll understand what happens when you "send crypto" and make informed decisions about how to store your assets.

---

## Part 1: How Wallets Actually Work

### Wallets Don't Hold Crypto

This is the biggest misconception. Your wallet doesn't store cryptocurrency like a physical wallet holds cash.

**Reality:** Your crypto lives on the blockchain. Your wallet stores the **private keys** that prove you own it.

Think of it like this:
- The blockchain is a giant public ledger saying "Address X owns 5 SOL"
- Your wallet holds the key that proves you control Address X
- The crypto never "moves" to your wallet—only ownership changes on the ledger

### The Key Pair System

Every wallet creates two mathematically linked keys:

**Private Key**
- A long random number (256 bits)
- Must be kept secret
- Proves you authorized transactions
- If someone gets it, they control your crypto

**Public Key (Address)**
- Derived mathematically from private key
- Safe to share with anyone
- Where people send you crypto
- Cannot be reversed to find private key

```
Private Key (SECRET)
   ↓ Mathematical derivation (one-way)
Public Key → Address (SHARE FREELY)
```

### Seed Phrases: Your Master Backup

When you create a wallet, you get a seed phrase (12-24 words):

```
abandon ability able about above absent absorb abstract
absurd abuse access accident account accuse achieve acid
```

**What it does:**
- Encodes your private key in human-readable words
- Can regenerate ALL your accounts on any wallet
- Industry standard (BIP39) works across all major wallets

**Critical rules:**
- Write it down on paper (not digital)
- Store in multiple secure locations
- NEVER share with anyone
- NEVER enter it on a website

If someone has your seed phrase, they have everything.

---

## Part 2: Types of Wallets

### Software Wallets (Hot Wallets)

Your private keys live on an internet-connected device.

**Browser Extensions:**
- Phantom, MetaMask, Backpack
- Live in your browser
- Convenient for daily transactions
- Connect directly to websites and apps

**Mobile Apps:**
- Phantom Mobile, Trust Wallet
- Keys stored on your phone
- Biometric authentication (fingerprint/face)
- More secure than computers (better app isolation)

**How they work:**
```
1. You create wallet → Keys generated locally
2. You connect to app → App requests permission
3. You approve transaction → Wallet signs with private key
4. Signed transaction → Broadcast to blockchain
5. Private key NEVER leaves your device
```

**Security level:** Good for everyday use, risky for large holdings.

### Hardware Wallets (Cold Wallets)

Physical devices that store keys offline.

**Examples:** Ledger, Trezor, Keystone

**How they work:**
```
1. Keys generated on device (offline)
2. Keys stored in tamper-resistant chip
3. To transact: Connect device → Verify on device screen → Approve
4. Device signs transaction internally
5. Only signed transaction leaves device
6. Private keys NEVER touch internet
```

**Why they're more secure:**
- Even if your computer has malware, keys are safe
- Physical button confirms transactions (no remote access)
- Screen shows exactly what you're signing

**Trade-off:** Less convenient. Cost $50-150. Required for high-value holdings.

### Comparison Table

| Type | Security | Convenience | Best For |
|------|----------|-------------|----------|
| **Browser Wallet** | Medium | High | Daily transactions |
| **Mobile Wallet** | Medium-High | High | Regular use |
| **Hardware Wallet** | Excellent | Low | Long-term storage |
| **Exchange** | Variable | Excellent | Trading (short-term) |

---

## Part 3: Custodial vs Non-Custodial

### Custodial: Someone Else Holds Your Keys

**Examples:** Coinbase, Binance, Kraken (exchanges)

**How it works:**
- You create account with email/password
- Exchange generates and stores your keys
- You see a "balance" in their interface
- To withdraw, you request transfer to your address

**Pros:**
- Easy to use (like a bank app)
- Password reset if forgotten
- Customer support available
- No key management responsibility

**Cons:**
- "Not your keys, not your coins"
- Exchange can freeze your account
- If exchange is hacked, you lose funds
- If exchange collapses (FTX), funds may be lost
- Regulatory seizure possible

### Non-Custodial: You Hold Your Keys

**Examples:** Phantom, MetaMask, Ledger

**How it works:**
- You generate your own keys
- Keys stored on your device only
- You sign transactions directly
- No middleman, no permission needed

**Pros:**
- True ownership
- No counterparty risk
- Censorship-resistant
- Full access to DeFi
- Privacy (no KYC for wallet creation)

**Cons:**
- You're fully responsible
- Lose seed phrase = lose everything
- No customer support
- Must understand security basics

### The Golden Rule

**Small amounts, active trading:** Custodial is fine (exchange)

**Significant savings, long-term holding:** Non-custodial required

**High-value holdings:** Hardware wallet + non-custodial

---

## Part 4: How Transactions Work

### Anatomy of a Transaction

When you send crypto, here's what actually happens:

```
Transaction Contents:
├─ From: Your address
├─ To: Recipient address
├─ Amount: How much to send
├─ Fee: Payment to validators
├─ Nonce: Transaction counter (prevents replay)
└─ Signature: Proof you authorized it
```

### The Transaction Lifecycle

**Step 1: Creation**
- You specify recipient and amount
- Wallet calculates fee
- Transaction data assembled

**Step 2: Signing**
- Wallet uses private key to create signature
- Signature proves authorization
- Private key never transmitted

**Step 3: Broadcasting**
- Signed transaction sent to network
- Reaches validator nodes
- Enters "mempool" (waiting room)

**Step 4: Inclusion**
- Validator includes transaction in block
- Block added to chain
- Transaction now "confirmed"

**Step 5: Finality**
- More blocks built on top
- After enough confirmations, considered final
- Cannot be reversed

### Transaction Speed by Network

| Network | Block Time | Typical Finality |
|---------|-----------|------------------|
| **Bitcoin** | ~10 min | ~60 min |
| **Ethereum** | ~12 sec | ~12 min |
| **Solana** | ~400 ms | ~20-40 sec |

Solana feels instant. Bitcoin requires patience.

### Transaction Fees

Every transaction requires a fee paid to validators.

**Bitcoin/Ethereum:** Fee varies with network congestion
- Busy network = higher fees
- Ethereum can spike to $50+ during peak times

**Solana:** Consistent low fees
- ~$0.00025 per transaction
- ~200,000 transactions for $1
- Fees rarely change

---

## Part 5: Addresses and Networks

### One Address Per Network

A Solana address ONLY works on Solana. An Ethereum address ONLY works on Ethereum.

**Common mistake:** Sending SOL to an Ethereum address
**Result:** Funds lost forever

**Always verify:**
1. You're on the correct network
2. Address format matches the network
3. Recipient expects this specific token

### Address Formats

Different networks have different address formats:

**Solana:** 32-44 characters, alphanumeric
```
7EYnhQoR9YM3N7UoaKRoA44Uy8JeaZV3qyouov87awMs
```

**Ethereum:** 42 characters, starts with 0x
```
0x742d35Cc6634C0532925a3b844Bc9e7595f2bD18
```

**Bitcoin:** Various formats, often starts with 1, 3, or bc1
```
bc1qar0srrr7xfkvy5l643lydnw9re59gtzzwf5mdq
```

### Test Transactions First

When sending to a new address:
1. Send a tiny amount first ($1 worth)
2. Confirm it arrived
3. Then send the full amount

The small fee is worth the peace of mind.

---

## Part 6: Security Best Practices

### Protecting Your Keys

**Do:**
- Write seed phrase on paper
- Store in multiple secure locations
- Use hardware wallet for large amounts
- Verify addresses before sending
- Use official wallet downloads only

**Don't:**
- Screenshot your seed phrase
- Store seed phrase in cloud/email
- Enter seed phrase on any website
- Share seed phrase with "support"
- Click suspicious links in DMs

### Common Scam Patterns

**Fake Support**
"Hi, I'm from Phantom support. Please verify your wallet by entering your seed phrase."
- Real support NEVER asks for seed phrases
- Always use official channels only

**Phishing Sites**
- Fake websites that look identical to real ones
- URL slightly different (phantom.io vs phantomm.io)
- Always bookmark official sites

**Malicious Approvals**
- Websites request "unlimited approval" for tokens
- They can drain your entire balance later
- Revoke unused approvals regularly

**Airdrop Scams**
- Random tokens appear in your wallet
- Interacting with them triggers malicious contract
- Ignore tokens you didn't expect

### Recovery Options

**Lost password (custodial):** Email reset, support ticket

**Lost password (non-custodial):** Use seed phrase to restore

**Lost seed phrase + access to wallet:** Create new wallet, transfer everything immediately, write down new seed phrase

**Lost seed phrase + lost wallet access:** Funds are gone. No recovery possible. This is why backups matter.

---

## Part 7: Choosing the Right Setup

### Beginner Setup

**Goal:** Start using crypto safely

**Recommendation:**
- Browser wallet (Phantom) for Solana
- Keep small amounts only (<$500)
- Learn by doing with small transactions

### Intermediate Setup

**Goal:** Regular crypto user

**Recommendation:**
- Hardware wallet (Ledger) for savings
- Software wallet for daily use
- Transfer to hardware monthly
- Keep <$1,000 in hot wallet

### Advanced Setup

**Goal:** Maximum security

**Recommendation:**
- Multiple hardware wallets
- Geographic distribution of seed backups
- Different wallets for different purposes
- Regular security audits

---

## Part 8: Practical Wallet Actions

### Creating a Wallet

1. Download from official source only
2. Generate new wallet (creates keys locally)
3. Write down seed phrase on paper
4. Verify by entering seed phrase
5. Store backup in secure location

### Connecting to Apps

1. App requests wallet connection
2. Wallet shows what permissions are requested
3. Review carefully before approving
4. You can disconnect anytime

### Signing Transactions

1. App prepares transaction
2. Wallet displays transaction details
3. Verify: recipient, amount, fees
4. Approve or reject
5. Once approved, cannot be undone

### Revoking Permissions

Over time, you'll have approved many apps. Periodically:
1. Review connected sites in wallet settings
2. Disconnect unused connections
3. Revoke token approvals you no longer need

---

## Summary

| Concept | Key Point |
|---------|-----------|
| **Wallets** | Store keys, not crypto |
| **Private keys** | Prove ownership; never share |
| **Seed phrase** | Master backup; write on paper |
| **Custodial** | Easy but you don't truly own |
| **Non-custodial** | True ownership, full responsibility |
| **Hardware wallet** | Best security for significant amounts |
| **Transactions** | Irreversible once confirmed |
| **Addresses** | Network-specific; verify before sending |

---

## What's Next?

Now that you understand wallets and transactions, the next document covers:
- **What you can do with crypto** (beyond sending)
- **DeFi basics: staking, swapping, earning yield**
- **How to evaluate opportunities**

Continue to: [03_DEFI_ESSENTIALS.md](./03_DEFI_ESSENTIALS.md)

---

## Quick Reference: Wallet Comparison

| Feature | Browser Wallet | Mobile Wallet | Hardware Wallet | Exchange |
|---------|---------------|---------------|-----------------|----------|
| **Security** | Medium | Medium-High | Excellent | Variable |
| **Convenience** | High | High | Low | Excellent |
| **Self-custody** | Yes | Yes | Yes | No |
| **DeFi access** | Full | Full | Full | Limited |
| **Cost** | Free | Free | $50-150 | Free |
| **Recovery** | Seed phrase | Seed phrase | Seed phrase | Password |
| **Best for** | Daily use | Regular use | Savings | Trading |

---

**Last Updated:** January 16, 2026
**Version:** 2.0
