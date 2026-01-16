# Crypto Foundations: What is Blockchain?

**Reading Time:** ~20 minutes
**Audience:** Complete Beginners
**Level:** Beginner
**Updated:** January 2026

---

## What You'll Learn

This document answers the fundamental question: **What is cryptocurrency?**

By the end, you'll understand:
- What a blockchain actually is (and isn't)
- Why cryptography makes it secure
- Key terms you'll see everywhere
- How different blockchains compare

No prior knowledge required. We start from zero.

---

## Quick Acronym Reference

| Acronym | What It Means |
|---------|---------------|
| **BTC** | Bitcoin |
| **ETH** | Ethereum |
| **SOL** | Solana |
| **PoW** | Proof of Work |
| **PoS** | Proof of Stake |
| **PoH** | Proof of History |

---

## Part 1: What is a Blockchain?

### The Simple Analogy

Imagine a ledger (an accounting book) that:
- **Multiple people maintain independently** (distributed)
- **No one can erase past entries** (immutable)
- **New entries are verified by the group before adding** (consensus)
- **Everyone has an identical copy** (decentralized)

If someone tries to cheat by changing an old entry, everyone else's copies would show the tampering. The fraudster would need to simultaneously change the majority's copies—mathematically impractical.

### The Technical Reality

A blockchain is a linked list of "blocks," where each block contains:
- **Transactions** (the data)
- **A cryptographic hash** (unique fingerprint)
- **The previous block's hash** (creates the chain)
- **A timestamp**

```
Block 1                Block 2                Block 3
├─ Txn A              ├─ Txn D              ├─ Txn G
├─ Txn B              ├─ Txn E              ├─ Txn H
├─ Txn C              ├─ Txn F              └─ Hash: 7F9A2...
├─ Hash: 3B4E1...     └─ Hash: 5C8D2...         ↑
└─ Prev: 0000...          ↑                     └─ (references Block 2's hash)
                        (references Block 1's hash)
```

Each block points to the previous one. Change anything in Block 1, and its hash changes. That breaks the reference in Block 2, which breaks Block 3, and so on. The whole chain becomes invalid.

### Why "Decentralized" Matters

**Traditional systems (banks):**
- One company controls the database
- They can freeze accounts, reverse transactions, change rules
- You trust them not to abuse that power

**Blockchain:**
- Thousands of computers maintain the same database
- No single entity controls it
- Rules are enforced by math, not promises

---

## Part 2: Why Cryptography Makes It Work

### Hashing: The One-Way Function

A hash function takes any input and produces a fixed-size string.

```
Input: "Hello World"
Output: 5EB63BBBE01EEED093CB22BB8F5ACDC3...
```

**Key properties:**
- Same input always produces same hash
- Change one character, completely different hash
- Impossible to reverse (can't get input from hash)

**Why it matters:** Hashes prove data hasn't been tampered with. If someone changes a transaction, the hash changes, and everyone notices.

### Digital Signatures: Proof of Authorization

Every crypto account has two keys:
- **Public Key:** Your account address (visible to everyone)
- **Private Key:** Secret password (only you know)

**How it works:**
1. You sign a transaction with your private key
2. This creates a digital signature
3. Anyone can verify the signature using your public key
4. They can confirm you authorized it—without seeing your private key

**Analogy:** Like signing a check. Everyone can verify your signature, but they can't forge it.

### Addresses: Your Account Number

A wallet address is derived from your public key.

**Example Solana address:**
```
9B5X32orMjHAGJjCjwuc9jVrKm86V5yc...
```

- Anyone can send crypto to this address
- Only the person with the private key can spend from it
- Addresses are public; private keys must stay secret

---

## Part 3: Essential Terminology

### Tokens & Cryptocurrencies

**Token**
Any digital asset on a blockchain. This includes cryptocurrencies (Bitcoin, Ethereum, SOL), utility tokens, governance tokens, and NFTs.

**Cryptocurrency**
Digital money that uses cryptography for security. The native tokens of blockchains (BTC, ETH, SOL) are cryptocurrencies.

**Stablecoin**
A cryptocurrency designed to maintain a stable value, usually pegged to $1 USD. Examples: USDC, USDT. Used to avoid crypto volatility while staying in the ecosystem.

### Network Terms

**Node**
A computer running blockchain software that maintains a copy of the ledger and validates transactions.

**Validator**
A node that actively participates in creating new blocks. They stake collateral and earn rewards for honest behavior.

**Transaction**
A request to move assets from one account to another, signed with the sender's private key.

**Block**
A bundle of transactions added to the chain. Contains transaction data, hashes, and timestamps.

**Gas / Transaction Fee**
The cost to execute a transaction. Paid to validators for processing your request.

### Time & Finality

**Block Time**
How long between blocks. Bitcoin: ~10 minutes. Ethereum: ~12 seconds. Solana: ~400 milliseconds.

**Finality**
The point where a transaction cannot be reversed. Different from block time—a transaction can be in a block but not yet final.

**Confirmation**
Additional blocks built on top of your transaction. More confirmations = higher confidence it won't be reversed.

| Blockchain | Block Time | Finality |
|------------|-----------|----------|
| Bitcoin | ~10 min | ~60 min (6 blocks) |
| Ethereum | ~12 sec | ~12-15 min |
| Solana | ~400 ms | ~20-40 sec |

### Ownership Terms

**Wallet**
Software that stores your private keys and lets you send/receive crypto. It doesn't hold your crypto—it holds the keys that prove ownership.

**Self-Custody**
You control your own private keys. No third party can freeze or access your funds. Higher responsibility, but true ownership.

**Custodial**
A third party (exchange, bank) holds your keys for you. Easier, but you trust them with your assets.

**Seed Phrase (Recovery Phrase)**
12-24 words that can regenerate your private keys. If you lose your keys but have the seed phrase, you can recover everything.

**NEVER share your seed phrase. Anyone who has it can take your crypto.**

---

## Part 4: How Blockchains Agree (Consensus)

The core problem: How do thousands of computers agree on what's true without a central authority?

### Proof of Work (PoW) - Bitcoin

**How it works:**
- Miners compete to solve complex math puzzles
- First to solve it proposes the next block
- Solving requires massive computational effort
- Winning earns block rewards + transaction fees

**Security:** To attack, you'd need more computing power than everyone else combined. The cost is astronomically high.

**Trade-off:** Uses enormous amounts of electricity (~211 TWh/year).

### Proof of Stake (PoS) - Ethereum

**How it works:**
- Validators lock up cryptocurrency as collateral
- Network randomly selects validators to propose blocks
- If they cheat, they lose their stake (slashing)
- Honest behavior earns rewards

**Security:** To attack, you'd need to buy 51% of all staked crypto. If caught, you lose everything.

**Trade-off:** Uses 99.9% less energy than PoW, but requires trusting economic incentives.

### Proof of History (PoH) - Solana

**How it works:**
- Combines PoS with a cryptographic timestamp system
- Transactions are ordered before consensus
- No waiting for validators to agree on timing
- Enables much faster processing

**Security:** Same economic security as PoS, plus computational cost to rewrite history.

**Trade-off:** Fastest option, but newest and less battle-tested.

### Comparison at a Glance

| Aspect | PoW (Bitcoin) | PoS (Ethereum) | PoH (Solana) |
|--------|---------------|----------------|--------------|
| **Speed** | ~7 TPS | ~15-30 TPS | ~65,000+ TPS |
| **Energy** | Very High | Very Low | Very Low |
| **Proven** | 16+ years | 3+ years | ~5 years |
| **Best For** | Store of value | DeFi ecosystem | Real-time apps |

---

## Part 5: Types of Tokens

### Native Tokens

The primary cryptocurrency of a blockchain:
- **BTC** on Bitcoin
- **ETH** on Ethereum
- **SOL** on Solana

Used for transaction fees and network security (staking).

### Stablecoins

Designed to maintain $1 value:

**USDC (USD Coin)**
- Backed by real US dollars in bank accounts
- Issued by Circle (regulated company)
- Most transparent, widely audited

**USDT (Tether)**
- Largest stablecoin by market cap
- Less transparent about reserves
- Higher risk, but very liquid

**DAI**
- Decentralized, backed by crypto collateral
- No company controls it
- More complex, but censorship-resistant

### Governance Tokens

Give voting rights on protocol decisions:
- **UNI** for Uniswap
- **JUP** for Jupiter
- Holders vote on upgrades, fee changes, treasury allocation

### Utility Tokens

Provide access to specific services:
- Pay for features within a protocol
- Access premium functionality
- Often used in gaming or social apps

---

## Part 6: Key Concepts to Remember

### "Not Your Keys, Not Your Coins"

If someone else holds your private keys (like an exchange), they control your crypto. Many people lost everything when exchanges collapsed (FTX, Mt. Gox).

**Recommendation:** Keep significant holdings in a wallet you control.

### Gas Fees Vary Wildly

| Network | Typical Fee |
|---------|-------------|
| Bitcoin | $1-10 |
| Ethereum | $2-50 |
| Solana | ~$0.00025 |

Solana is ~10,000x cheaper than Ethereum for simple transactions.

### Transactions Are Irreversible

Once confirmed, crypto transactions cannot be undone. There's no bank to call, no dispute process. Send to the wrong address = funds are gone.

**Always double-check addresses before sending.**

### Different Chains, Different Addresses

A Solana address only works on Solana. An Ethereum address only works on Ethereum. Sending SOL to an ETH address = lost forever.

**Make sure you're using the right network.**

---

## Summary

| Concept | Key Point |
|---------|-----------|
| **Blockchain** | Distributed ledger that can't be tampered with |
| **Cryptography** | Math that proves ownership and prevents fraud |
| **Tokens** | Digital assets living on blockchains |
| **Consensus** | How networks agree without central authority |
| **Wallets** | Software that holds your keys (not your crypto) |
| **Self-custody** | You control the keys = you own the assets |

---

## What's Next?

Now that you understand what blockchain is, the next document covers:
- **How wallets actually work**
- **Sending and receiving transactions**
- **Different types of custody**

Continue to: [02_HOW_CRYPTO_WORKS.md](./02_HOW_CRYPTO_WORKS.md)

---

## Glossary Quick Reference

| Term | Definition |
|------|------------|
| **Address** | Public identifier for receiving crypto |
| **Block** | Bundle of transactions added to the chain |
| **Blockchain** | Distributed, immutable digital ledger |
| **Consensus** | How networks agree on truth |
| **Finality** | When a transaction becomes irreversible |
| **Gas** | Transaction fee paid to validators |
| **Hash** | Cryptographic fingerprint of data |
| **Node** | Computer running blockchain software |
| **Private Key** | Secret that proves ownership |
| **Public Key** | Address derived from private key |
| **Seed Phrase** | Words that can recover your keys |
| **Stablecoin** | Token pegged to $1 USD |
| **Token** | Any digital asset on blockchain |
| **Validator** | Node that creates new blocks |
| **Wallet** | Software holding your private keys |

---

**Last Updated:** January 16, 2026
**Version:** 2.0
