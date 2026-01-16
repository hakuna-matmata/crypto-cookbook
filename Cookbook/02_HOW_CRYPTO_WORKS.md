# How Crypto Works: Wallets, Transactions & Custody

**Reading Time:** ~35 minutes
**Audience:** Beginners ready for practical knowledge
**Level:** Beginner
**Updated:** January 2026

---

## Table of Contents

1. [What You'll Learn](#what-youll-learn)
2. [Part 1: How Wallets Actually Work](#part-1-how-wallets-actually-work)
   - [Wallets Don't Hold Crypto](#wallets-dont-hold-crypto)
   - [The Key Pair System](#the-key-pair-system)
   - [Seed Phrases: Your Master Backup](#seed-phrases-your-master-backup)
   - [Key Derivation (HD Wallets)](#key-derivation-hd-wallets)
3. [Part 2: Types of Wallets](#part-2-types-of-wallets)
   - [Software Wallets (Hot Wallets)](#software-wallets-hot-wallets)
   - [Hardware Wallets (Cold Wallets)](#hardware-wallets-cold-wallets)
   - [Browser Extension Wallets](#browser-extension-wallets)
   - [Mobile App Wallets](#mobile-app-wallets)
4. [Part 3: Custodial vs Non-Custodial](#part-3-custodial-vs-non-custodial)
   - [Custodial: Someone Else Holds Your Keys](#custodial-someone-else-holds-your-keys)
   - [Non-Custodial: You Hold Your Keys](#non-custodial-you-hold-your-keys)
   - [Complete Custody Comparison](#complete-custody-comparison)
5. [Part 4: How Transactions Work](#part-4-how-transactions-work)
   - [Anatomy of a Transaction](#anatomy-of-a-transaction)
   - [The Transaction Lifecycle](#the-transaction-lifecycle)
   - [Commitment Levels (Solana)](#commitment-levels-solana)
6. [Part 5: Addresses and Networks](#part-5-addresses-and-networks)
7. [Part 6: Security Best Practices](#part-6-security-best-practices)
8. [Part 7: Choosing the Right Setup](#part-7-choosing-the-right-setup)
9. [Part 8: Practical Wallet Actions](#part-8-practical-wallet-actions)
10. [Summary](#summary)

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

**Key distinction**: A wallet is NOT a bank account. You own the keys; you own the crypto. If you lose the keys, the crypto is gone forever (no password reset).

### The Key Pair System

Every wallet creates two mathematically linked keys:

**Private Key**
- A long random number (256 bits)
- A secret number that proves ownership and authorizes transactions
- Must be kept secret—equivalent to a password, but mathematically tied to your account address
- If exposed: full account compromise

**Public Key (Address)**
- Derived mathematically from private key using elliptic curve mathematics
- Safe to share with anyone
- Where people send you crypto
- Cannot be reversed to find private key

```
Private Key (SECRET)
   ↓ Mathematical derivation (one-way)
Public Key → Address (SHARE FREELY)
```

**Example Solana address:**
```
9B5X32orMjHAGJjCjwuc9jVrKm86V5yc...
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

**Why it works:**
- Words derived from entropy (randomness)
- You can recreate the same private key from these words on any wallet
- If device breaks, import seed phrase into new wallet → same keys

**Critical rules:**
- Write it down on paper (not digital)
- Store in multiple secure locations
- NEVER share with anyone
- NEVER enter it on a website

**Security rule: NEVER share seed phrase. Seed phrase = full access to all funds.**

### Key Derivation (HD Wallets)

From one seed phrase, you can generate unlimited addresses for unlimited cryptocurrencies.

**How it works:**
```
Seed phrase (BIP39)
  ↓
Master key
  ↓
Derivation path (m/44'/501'/0'/0')  [This means: Solana, account 0, address 0]
  ↓
Private key for that address
  ↓
Public key (address)
```

**Why this matters:**
- One seed phrase generates all your Solana addresses
- Same seed works on Bitcoin, Ethereum, Solana (if wallet supports it)
- Wallets can be recovered with just the seed phrase

---

## Part 2: Types of Wallets

### Software Wallets (Hot Wallets)

Your private keys live on an internet-connected device. Keys stored on your device (phone, computer, browser) as encrypted data. Keys live on same device as internet connection—security depends on device security.

**Browser Extensions:**
- Phantom, MetaMask, Backpack, Solflare
- Live in your browser
- Convenient for daily transactions
- Connect directly to websites and apps

**Mobile Apps:**
- Phantom Mobile, Trust Wallet, Solflare Mobile
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

Physical devices (USB stick-like) that securely store private keys offline. Keys never leave the device; you sign transactions on-device and broadcast signed data (not keys) to blockchain.

**Examples:**
- **Ledger** (most popular, 5M+ users)
- **Trezor** (strong privacy/open-source focus)
- **Coldcard** (Bitcoin-focused, highly secure)
- **Keystone** (air-gapped, no USB connection)

**How they work:**
```
1. Keys generated on device (offline)
2. Keys stored in tamper-resistant chip (secure enclave)
3. To transact: Connect device → Verify on device screen → Approve
4. Device signs transaction internally
5. Only signed transaction leaves device
6. Private keys NEVER touch internet
```

**Security model:**
- Keys stored in secure enclave (tamper-resistant chip)
- Signing happens on-device (malware on your computer can't steal keys)
- Display on device (verify transaction before signing, not relying on computer screen)
- Seed backup: If device breaks, recover with seed phrase on new device

**Why they're more secure:**
- Even if your computer has malware, keys are safe
- Physical button confirms transactions (no remote access)
- Screen shows exactly what you're signing

**Trade-off:** Less convenient. Cost $50-150. Required for high-value holdings.

**Solana-specific hardware wallet support:**
- Ledger: Full support (most used)
- Trezor: Full support
- Keystone: Support via QR code (air-gapped)

### Browser Extension Wallets

Private keys stored encrypted in browser storage. Sign transactions in popup when dApps request permission.

**How it works:**
```
1. Create wallet → Private key generated locally → Stored encrypted in browser
2. Connect to dApp → dApp requests permission to send transaction
3. You review and approve in wallet popup
4. Wallet signs transaction locally
5. Signed transaction broadcast to blockchain
```

**Security:**
- ✓ Keys never leave your device
- ✓ dApp doesn't see private key (only gets signature)
- ❌ Keys stored on internet-connected device (vulnerable to malware)
- ❌ Browser extensions can be compromised

**Solana ecosystem:**
- **Phantom** (~15M users): Dominant Solana wallet
- **Solflare** (~4M users): #2 Solana wallet, focus on security (transaction preview, phishing detection)
- **TrustWallet**: Multi-chain, owned by Binance

### Mobile App Wallets

Private keys stored on phone's secure enclave (if available). More secure than computers (phones have stronger isolation).

**Security improvements over computers:**
- Phone OS isolates apps better than computer browsers
- Some phones (iPhone with Secure Enclave) store keys in tamper-resistant hardware
- Biometric auth (face/fingerprint) more convenient than passwords

### Wallet Comparison Table

| Type | Security | Convenience | Best For |
|------|----------|-------------|----------|
| **Browser Wallet** | Medium | High | Daily transactions |
| **Mobile Wallet** | Medium-High | High | Regular use |
| **Hardware Wallet** | Excellent | Low | Long-term storage |
| **Exchange** | Variable | Excellent | Trading (short-term) |

---

## Part 3: Custodial vs Non-Custodial

### Custodial: Someone Else Holds Your Keys

Third party (exchange, institution, or service) holds your private keys on your behalf. You access crypto through their app/platform, but they control the keys.

**Examples:**
- **Centralized exchanges**: Binance, Kraken, Coinbase (you hold coins on exchange)
- **Trading platforms**: Robinhood, eToro
- **Custodial services**: PayPal, Square (limited crypto features)

**How it works:**
```
You send crypto → Exchange receives your crypto
Exchange stores your keys in their vault
You withdraw by requesting from exchange
Exchange transfers to your address
```

**Pros:**
- Easy to use (familiar UI like banking apps)
- No key management required (no lost keys)
- Customer support available
- Can freeze suspicious accounts (safety)

**Cons:**
- **Counterparty risk**: Exchange can be hacked (Mt. Gox lost $450M, FTX collapsed)
- **Regulatory risk**: Funds can be frozen by authorities or seized
- **Not your keys, not your coins**: You don't technically own the crypto until you withdraw
- **Lower yield**: Platforms take cut of staking/lending returns

### Non-Custodial: You Hold Your Keys

You hold your own private keys. You control the crypto directly on the blockchain. No third party can prevent you from sending/receiving.

**Examples:**
- **Software wallets**: MetaMask, Phantom, Solflare, TrustWallet
- **Hardware wallets**: Ledger, Trezor, Coldcard
- **Browser wallets**: Brave wallet
- **Self-hosted**: Running your own node with full control

**How it works:**
```
You generate private keys (stored in your device/vault)
You sign transactions locally with your keys
You broadcast signed transaction to blockchain
Blockchain processes it without intermediary
```

**Pros:**
- **True ownership**: You control the keys, you control the funds
- **No counterparty risk**: No exchange can be hacked to steal your funds
- **Censorship-resistant**: No authority can freeze your account
- **Better yield**: Direct access to DeFi protocols
- **Composability**: Can use same keys across multiple dApps (DeFi, NFTs, staking)

**Cons:**
- **Key management burden**: You're responsible for backups
- **Loss is permanent**: Lose seed phrase = funds gone forever
- **User error risk**: Sending to wrong address, phishing, malware
- **Less support**: Wallets provide limited customer support
- **Slower onboarding**: More setup required

### The Golden Rule

**Small amounts, active trading:** Custodial is fine (exchange)

**Significant savings, long-term holding:** Non-custodial required

**High-value holdings:** Hardware wallet + non-custodial

### Complete Custody Comparison

| Aspect | Custodial (CEX) | Software Wallet | Hardware Wallet |
|--------|-----------------|-----------------|-----------------|
| **Key Control** | Exchange holds | You hold | You hold |
| **Owner Risk** | Hacks, freezing, collapse | Malware, phishing, lost seed | Lost device, lost seed |
| **Security Level** | Medium (professional security, but centralized target) | Good (keys isolated from signing) | Excellent (keys offline) |
| **Speed** | Instant (on exchange) | 1-3 seconds | 10-30 seconds (device interaction) |
| **Convenience** | Excellent (like banking app) | Very good (built-in dApp browser) | Good (but device required) |
| **DeFi Access** | Limited | Full access to all DeFi | Full access with device |
| **Cost** | Fees per transaction/trading | Free (except network gas) | $50-150 upfront |
| **Withdrawal Time** | Hours-days (requires KYC) | Seconds to minutes | Seconds to minutes |
| **Censorship Risk** | High (authority can freeze) | None (you control keys) | None (you control keys) |
| **Best For** | Day traders, beginners, fiat on/off | Active DeFi users, long-term holders | High-value holdings, maximum security |

### Hardware vs Software Seed Storage

| Storage Method | Security | Recovery | Convenience | Cost |
|----------------|----------|----------|-------------|------|
| **Hardware wallet + paper seed** | ★★★★★ (keys offline) | ✓ (seed as backup) | ★ (device required) | $50-150 |
| **Software wallet (browser)** | ★★★ (keys on internet device) | ✓ (seed phrase backup) | ★★★★ (always available) | Free |
| **Software wallet (mobile)** | ★★★★ (phone isolation) | ✓ (seed phrase backup) | ★★★★★ (most convenient) | Free |
| **Paper wallet** | ★★★★★ (fully offline) | ✗ (fragile) | ★ (must type manually) | Free |
| **Centralized exchange** | ★★ (counterparty risk) | N/A (you don't own keys) | ★★★★★ (easiest) | Free (but fees) |

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

### Commitment Levels (Solana)

Solana does NOT use "confirmations" like Bitcoin. Instead uses **commitment levels** indicating transaction state with increasing confidence:

**1. Processed** (~400ms)
- Transaction included in current block but not yet voted on
- Risk: ~5% chance transaction drops if cluster forks

**2. Confirmed** (~1-2 seconds)
- Block has been voted on by supermajority of stake-weighted validators (≥66%)
- Near-zero fork risk; no confirmed block has ever reverted in Solana's history

**3. Finalized** (~10-20 seconds)
- Block has 32-slot lock-out (31+ additional confirmed blocks built on top)
- Absolute economic finality; reversal would require >33% of network stake colluding (economically irrational)

**Why the distinction matters**: Bitcoin's "6 confirmations" means sequential computational work. Solana's "finalized commitment level" means validator consensus + time lock. Different security models, not directly comparable. Always specify "commitment level" for Solana, not "confirmations."

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
- Browser wallet (Phantom or Solflare) for Solana
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

### When to Recommend What

- **Beginner, wants simplicity**: Phantom or Solflare (browser wallet)
- **High security, rarely trades**: Hardware wallet (Ledger) + software wallet for active trading
- **Active trading, lots of transactions**: Software wallet (lower friction)
- **Long-term hold, paranoid**: Hardware wallet with paper seed backup

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
| **HD Wallets** | One seed phrase generates unlimited addresses |
| **Custodial** | Easy but you don't truly own |
| **Non-custodial** | True ownership, full responsibility |
| **Hardware wallet** | Best security for significant amounts |
| **Transactions** | Irreversible once confirmed |
| **Commitment levels** | Solana's version of confirmations (processed → confirmed → finalized) |
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
