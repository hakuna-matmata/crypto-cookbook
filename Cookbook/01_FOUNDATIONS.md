# Crypto Foundations: What is Blockchain?

**Reading Time:** ~35 minutes
**Audience:** Complete Beginners to Intermediate
**Level:** Beginner
**Updated:** January 2026

---

## Table of Contents

1. [What You'll Learn](#what-youll-learn)
2. [Quick Acronym Reference](#quick-acronym-reference)
3. [Part 1: What is a Blockchain?](#part-1-what-is-a-blockchain)
   - [The Simple Analogy](#the-simple-analogy)
   - [The Technical Reality](#the-technical-reality)
   - [Why Decentralized Matters](#why-decentralized-matters)
4. [Part 2: Why Cryptography Makes It Work](#part-2-why-cryptography-makes-it-work)
   - [Hashing: The One-Way Function](#hashing-the-one-way-function)
   - [Digital Signatures: Proof of Authorization](#digital-signatures-proof-of-authorization)
   - [Addresses: Your Account Number](#addresses-your-account-number)
5. [Part 3: Essential Terminology](#part-3-essential-terminology)
   - [Tokens & Cryptocurrencies](#tokens--cryptocurrencies)
   - [Network Terms](#network-terms)
   - [Time & Finality](#time--finality)
   - [Ownership Terms](#ownership-terms)
6. [Part 4: How Blockchains Agree (Consensus)](#part-4-how-blockchains-agree-consensus)
   - [Proof of Work (PoW) - Bitcoin](#proof-of-work-pow---bitcoin)
   - [Proof of Stake (PoS) - Ethereum](#proof-of-stake-pos---ethereum)
   - [Proof of History (PoH) - Solana](#proof-of-history-poh---solana)
   - [The Three Mechanisms in Plain English](#the-three-mechanisms-in-plain-english)
   - [Consensus Mechanism Comparison](#consensus-mechanism-comparison)
7. [Part 5: Types of Tokens](#part-5-types-of-tokens)
8. [Part 6: Key Concepts to Remember](#part-6-key-concepts-to-remember)
9. [Summary](#summary)
10. [Glossary Quick Reference](#glossary-quick-reference)

---

## What You'll Learn

This document answers the fundamental question: **What is cryptocurrency?**

By the end, you'll understand:
- What a blockchain actually is (and isn't)
- Why cryptography makes it secure
- Key terms you'll see everywhere
- How different blockchains compare
- Detailed mechanics of consensus mechanisms

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
| **VDF** | Verifiable Delay Function |
| **TPS** | Transactions Per Second |
| **TWh** | Terawatt-hours |

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
A computer running blockchain software that maintains a copy of the ledger and validates transactions. In Solana: ~1,295 nodes across 45+ countries.

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
The point at which reverting a transaction would require economically irrational behavior by the network. Key distinction: finality ≠ block time. A transaction in a block doesn't mean it's final.

- **Bitcoin**: Probabilistic finality. Commonly assumed after ~6 blocks (~60 minutes). Each additional block reduces reorg probability.
- **Ethereum**: Economic finality via Casper FFG. ~12–15 minutes (2 epochs). Block inclusion at 12 seconds is NOT finality.
- **Solana**: Economic finality via stake-weighted voting. ~20–40 seconds. Slot time is 400ms, but finality requires network consensus.

**Confirmation**
Additional blocks or votes that increase confidence a transaction will not be reverted.

- **Bitcoin**: Each confirmation ≈ 10 minutes (one additional block). 6 confirmations (~60 minutes) is the common safety standard.
- **Solana**: Uses "commitment levels" instead: processed (~400ms), confirmed (~1-2 seconds), and finalized (~10-20 seconds).

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

The core problem consensus solves: **How do distributed participants agree on truth without a central authority?**

### Proof of Work (PoW) - Bitcoin

#### The Setup: A Very Dumb But Very Expensive Lottery

Imagine this: Bitcoin is like a lottery, but instead of picking lucky numbers, miners are doing billions of pointless calculations.

**What the miner has:**
- A block of pending transactions (e.g., Alice → Bob: 0.1 BTC, Charlie → Dana: 0.3 BTC, etc.)
- A block header containing:
  - Hash of the previous block (links the chain)
  - Timestamp
  - A nonce (a random number miners twist to try different combinations)

**The rule (this is the "work" part):**
Bitcoin says: "Find a hash of this block that starts with a certain number of zeros."

Example target (simplified):
```
000000000000000xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

**Important:**
- Hash = SHA-256 (one-way, unpredictable—no formula exists)
- You cannot calculate the right nonce
- You can only guess and check, billions of times per second

#### The Loop: What Miners Actually Do

```
Miner sets nonce = 1
Hashes the block → 9f3a7c1e... ❌ (doesn't start with enough zeros)

Miner sets nonce = 2
Hashes again → a41b92dd... ❌

Miner does this billions of times per second:
nonce = 18,392,884,113
hash = 0000000000000008af3c91... ✅

🎉 Winner. Stop.
```

#### What Happens When a Miner Wins

**The miner:**
1. Broadcasts the block + winning hash to the network
2. Receives the block reward (~3.125 BTC) + transaction fees

**Other nodes:**
1. Verify the hash in seconds (cheap to check)
2. Agree: "Yep, that hash is valid"
3. Add block to their copy of the chain

#### Why This Secures Bitcoin: The Key Insight

To cheat (e.g., rewrite transaction history), an attacker would have to:

1. Redo the Proof of Work for this block
2. AND redo it for every block after it
3. Faster than the rest of the world combined

**That means:**
- Insane hardware investment (millions of dollars)
- Insane electricity cost (hundreds of millions daily)
- And still probably fail

**Truth bomb:** Proof of Work doesn't stop cheating by rules—it stops cheating by making it **financial suicide**.

#### Energy Economics

**2025 Reality:**
- Bitcoin mining consumes ~211.58 TWh annually (0.83% of global electricity)
- Equivalent to Thailand's or Vietnam's entire electricity consumption
- BUT: 52.4% comes from renewable energy (42.6% renewable + 9.8% nuclear)
- **Comparison to other chains**: Ethereum (post-PoS) uses ~0.01 TWh annually—Bitcoin uses roughly **21,000x MORE energy** than Ethereum

**Why so energy-intensive?**
The security comes from computational cost. To attack Bitcoin, attackers would need:
- 51% of mining hashrate (combined computer power)
- Requires purchasing/renting millions of specialized computers
- Daily electricity costs: hundreds of millions of dollars
- Economic infeasibility makes the network secure

#### PoW Strengths & Weaknesses

| Aspect | Details |
|--------|---------|
| **Security** | Proven for 16+ years. Attack cost is astronomical. |
| **Decentralization** | Anyone with hardware can participate. High barrier to entry but distributed. |
| **Finality** | Probabilistic: 1 block ≈ 10 min. 6 confirmations (~60 min) assumed "final". |
| **Energy** | Massive consumption. Climate concerns legitimate. |
| **Scalability** | Limited by block time (10 min) and size (1MB). Bitcoin: ~7 TPS. |

---

### Proof of Stake (PoS) - Ethereum

#### The Setup: A Lottery Where You Risk Your Own Money

This is the opposite of PoW. Instead of wasting electricity, you put up collateral (your own money).

**What a validator has:**
- 32 ETH (~$100K) locked as collateral in a smart contract
- Ability to propose blocks and vote on their validity
- The risk: Misbehave, and you lose your ETH (slashing)

**The rule (this is the "stake" part):**
Ethereum says: "Validators with more stake have higher probability of being selected to propose the next block. But we'll randomize it so you can't predict who's next."

**Important:**
- Selection is stake-weighted (1,000 ETH → 100x more likely than 10 ETH)
- But not deterministic (you can't guarantee you'll propose next)
- Validators earn rewards for honest behavior, lose stake for dishonest behavior

#### The Loop: What Validators Actually Do

```
Slot 1 (12 seconds):
- Validator 2,847 is randomly selected as "proposer"
- They collect pending transactions into a block
- They broadcast: "Here's my proposed block" ✅

Other 1,000,000 validators:
- Check: "Is this block valid?" (takes ~1 second)
- Vote: "Yes, I attest this is valid" or "No, something's wrong"
- ~2/3 of validators attest = block is finalized ✅

Validator 2,847:
- Receives block reward (~0.03 ETH) + transaction fees
- Their stake: still safe (they behaved honestly)

🎉 Block added to chain. Next slot begins.
```

**If a validator misbehaves:**

```
Validator 2,847 tries to cheat:
- Proposes two different blocks at slot 1 (equivocation)
- Network detects contradiction

Punishment:
- 1% of their stake removed (at minimum)
- If many validators cheat simultaneously, penalty up to 100%
- Example: 32 ETH → 31.68 ETH gone (misbehavior caught early)

Reality check:
- Sept 2025: 39 validators slashed in one event
- Total loss: Several million dollars
```

#### Why This Secures Ethereum: The Key Insight

To cheat (e.g., rewrite transaction history), an attacker would have to:

1. Control 51% of all staked ETH
2. Without being detected (validators monitor each other)
3. Even if undetected, slashing would destroy their collateral
4. Worse than cheating: If detected during attack, lose 100% of stake

**That means:**
- Need ~$15B in ETH (51% of ~$29B total staked)
- Slashing penalty = automatic confiscation
- Market knows you cheated → ETH value crashes → you lose money twice

**Truth bomb:** Proof of Stake doesn't stop cheating by difficulty—it stops cheating by making it **economically suicidal AND automatic**.

#### Validator Rewards (2025 Data)

**Economics:**
- Average APY (Annual Percentage Yield): 3.2% (declining trend)
- If validator earns 3% on 32 ETH: +0.96 ETH/year (~$3,100)
- Fee: Network transaction fees added on top
- Trend: Rewards declining as more validators join (share the pie)

**Market Structure:**
- **Solo stakers** (<1%): 32 ETH deposit yourself, run validator software
- **Staking pools** (17.7%): Aggregate capital, earn pooled rewards minus commission
- **Liquid staking** (31.1%): Deposit assets → receive LST (stETH, etc.) → stake elsewhere
- **Top players**: Lido (47% of liquid staking market), Binance, Rocket Pool

#### Slashing: Punishment for Bad Behavior

**What Gets You Slashed:**
1. **Equivocation**: Proposing multiple blocks at same height (two different versions)
2. **Attestation violation**: Voting contradictory messages about block validity

**Penalty Tiers:**
- **Minor violation**: 1% of stake removed
- **Major violation**: Cascading penalty up to 100% (if many validators slashed simultaneously)

**Real Event (September 2025):**
- 39 validators slashed in largest correlated event since Ethereum's PoS launch
- Root cause: Third-party staking infrastructure (SSV Network) had configuration issues
- This demonstrates: Risk exists even when individual validators behave correctly

#### PoS Strengths & Weaknesses

| Aspect | Details |
|--------|---------|
| **Energy** | 0.01% of PoW energy. ~$2,700/year per validator vs millions for PoW. |
| **Accessibility** | 32 ETH barrier, but staking pools democratize access. |
| **Capital Efficiency** | Deposit = long-term commitment. Earning rewards, not wasting electricity. |
| **Slashing Risk** | Validator must trust their infrastructure (client software, hardware). |
| **Finality** | Faster than PoW (~12 seconds per slot, not ~10 minutes). |

---

### Proof of History (PoH) - Solana

#### The Setup: A Cryptographic Timestamp, Not a Lottery

This is radically different from PoW and PoS. Instead of "who gets to propose the next block?", PoH says: "Let's make time itself part of the blockchain."

**What the validator has:**
- Pending transactions from the network
- A powerful hash function (SHA-256)
- No special rights (yet—just the ability to propose)
- A slot (400 milliseconds) to do this

**The rule (this is the "proof of history" part):**
Solana says: "The leader continuously hashes the most recent state with incoming transactions, creating a sequential chain of hashes (H₀ → H₁ → H₂...). This produces ~4 billion sequential hashes per 400ms slot. Each transaction is cryptographically anchored at a specific hash index. If you try to reorder a transaction, the hash sequence from that point onward becomes invalid. Everyone can verify this immediately."

**Important:**
- This is NOT a lottery—it's deterministic sequencing
- The hashing takes ~400ms (unavoidable)
- But once done, the sequence is cryptographically **permanent**
- You cannot insert a transaction "between" two existing ones without redoing everything after

#### The Cryptographic Clock: How PoH Works

PoH is based on a **sequential hash function that cannot be sped up or parallelized**.

**Hash sequence (mathematical proof of elapsed time):**

```
H₀ = seed (starting point)
H₁ = SHA-256(H₀)
H₂ = SHA-256(H₁)
H₃ = SHA-256(H₂)
H₄ = SHA-256(H₃)
...
H₁₀,₀₀₀,₀₀₀ = SHA-256(H₉,₉₉₉,₉₉₉)
```

**Properties:**

- **Sequential**: You must compute every step in order. Can't skip H₂ and jump to H₄.
- **Time-enforcing**: If H₄ exists, then H₁, H₂, H₃ MUST have been computed before it.
- **Cheap to verify**: Anyone can replay and check instantly.

**This turns time into math.** No clock needed. No trust needed. Just cryptography.

#### How Transactions Get Ordered (The Leader's Job)

The leader continuously computes the hash chain while transactions arrive and anchors each transaction into it.

**Example:**

```
Tx A arrives → anchored at H₂
Tx B arrives → anchored at H₄
Tx C arrives → anchored at H₆
```

This cryptographically proves:
- Tx A happened before Tx B (H₂ before H₄)
- Tx B happened before Tx C (H₄ before H₆)
- Leader could NOT backdate or reorder (would need to recompute entire hash sequence)

Validators later replay:
```
H₀ → H₁ → H₂ → H₃ → H₄ → H₅ → H₆ → ...
               ↑              ↑
              Tx A           Tx B
```

**No timestamps. No debates. Just math.**

#### The Loop: What the Leader Actually Does

```
Leader receives pending transactions at slot 1000:
- Txn A: Alice → Bob: 1 SOL
- Txn B: Charlie → Dana: 2 SOL
- Txn C: Eve → Frank: 0.5 SOL

Leader applies Verifiable Delay Function (VDF):
- Hash(state + Txn A) = 0x8f2a1... (timestamp = 1000.0ms)
- Hash(0x8f2a1... + Txn B) = 0x3c4b7... (timestamp = 1000.1ms)
- Hash(0x3c4b7... + Txn C) = 0x5e9d2... (timestamp = 1000.2ms)

Broadcasts: "Block with sequence: A → B → C, hashes: 8f2a1 → 3c4b7 → 5e9d2" ✅

Other validators verify (takes milliseconds):
- "Let me hash the same inputs with VDF..."
- "Yep, the sequence matches. Block is valid." ✅

🎉 Block added to chain instantly (no voting needed for ordering).
```

**If someone tries to cheat:**

```
Attacker tries to insert Transaction X between A and B:
- Would need: Hash(0x8f2a1... + Txn X) = new intermediate hash
- Then: Hash(new_intermediate + Txn B) = different hash than 0x3c4b7...
- But then: Hash(different + Txn C) = different than 0x5e9d2...
- And every block AFTER this one would have different hashes
- Network would immediately detect: "Your hashes don't match!" ❌

The entire chain history would need to be rewritten.
```

#### End-to-End Execution Example (Real Scenario)

Let's watch PoS + PoH + Ledger rules work together on actual transactions.

**Initial state (before any transactions):**

```
Alice   = 100 SOL
Bob     = 10 SOL
Charlie = 50 SOL
Diana   = 0 SOL
```

**Transactions that arrive at the leader (in this order):**

```
1. Charlie → Diana: 25 SOL  (arrives at H₁₀₀)
2. Bob → Diana: 15 SOL       (arrives at H₂₀₀)
3. Alice → Bob: 20 SOL       (arrives at H₃₀₀)
```

**Validators replay and enforce ledger rules:**

```
Transaction 1: Charlie → Diana (25 SOL)
├─ Attached at H₁₀₀
├─ Charlie has 50 SOL ✅
├─ 50 ≥ 25 ✅
└─ Result: ✅ VALID

  Charlie = 50 - 25 = 25 SOL
  Diana   = 0 + 25  = 25 SOL
```

```
Transaction 2: Bob → Diana (15 SOL)
├─ Attached at H₂₀₀
├─ Bob has 10 SOL ❌
├─ 10 < 15 ❌
└─ Result: ❌ INVALID (insufficient balance)

  State does NOT change
  Bob   = 10 SOL (unchanged)
  Diana = 25 SOL (unchanged)

  Block continues (failed txns included but have no effect)
```

```
Transaction 3: Alice → Bob (20 SOL)
├─ Attached at H₃₀₀
├─ Alice has 100 SOL ✅
├─ 100 ≥ 20 ✅
└─ Result: ✅ VALID

  Alice = 100 - 20 = 80 SOL
  Bob   = 10 + 20  = 30 SOL
```

**Final canonical state (after all validators replay):**

```
Alice   = 80 SOL
Bob     = 30 SOL
Charlie = 25 SOL
Diana   = 25 SOL
```

#### Why This Secures Solana: The Key Insight

To cheat (e.g., reorder transactions), an attacker would have to:

1. Recompute all PoH hashes from the attack point forward
2. Do it faster than the rest of the network (which is still moving forward)
3. Convince the network their chain is the "real" one

**That means:**
- Need 51% of network validation power (like PoS)
- PLUS massive computational power to recompute PoH hashes
- PLUS do it all faster than the honest network
- Even then, longest chain always wins

**Truth bomb:** Proof of History doesn't stop cheating by electricity OR collateral—it stops cheating by making **rewriting the past computationally impossible before the future arrives**.

#### The Mental Model (Keep This)

```
PoS decides who may speak.
PoH proves the order of speech.
Validators enforce reality.
Everything else is implementation detail.
```

#### PoH Strengths & Weaknesses

| Aspect | Details |
|--------|---------|
| **Speed** | 400ms block/slot time; ~20-40s economic finality; ~1-2s practical safety. Enables real-time applications. |
| **Energy** | Hybrid with PoS = minimal energy. |
| **Scalability** | 65K+ TPS. Built-in capacity for ecosystem growth. |
| **Complexity** | VDF mechanism harder to understand than PoW/PoS. |
| **Validator Consolidation** | Requires quality validators (not commodity). Fewer validators (~800 vs. 1M+). |
| **Novelty** | Only ~5 years live. Less battle-tested than PoW/PoS. |

---

### The Three Mechanisms in Plain English

**If you had to explain each to your mom:**

**Proof of Work (Bitcoin):**
"People use super-expensive computers to solve puzzles. Whoever solves it first gets money. If you try to cheat, you'd need more computers than everyone else combined—which costs way more than you could ever steal. So nobody cheats."

**Proof of Stake (Ethereum):**
"People lock up their money as collateral, like posting bail. The network picks one person to propose the next block. If they're honest, they keep their money + get a reward. If they cheat, their money gets taken automatically. So it's cheaper than PoW, but you lose everything if you misbehave."

**Proof of History (Solana):**
"A leader creates a tamper-proof ordering by continuously hashing transaction data sequentially (~4 billion hashes per 400ms slot). Each transaction is cryptographically anchored at a specific hash index. If you try to insert a transaction out of order, the hash sequence from that point onward becomes invalid. Everyone can verify this immediately. You can't reorder transactions without redoing all subsequent hashes, and by then the network has moved on."

---

### Consensus Mechanism Comparison

| Aspect | **Proof of Work (Bitcoin)** | **Proof of Stake (Ethereum)** | **Proof of History (Solana)** |
|--------|---------------------------|---------------------------|--------------------------|
| **Core Idea** | Burn electricity to prove you did computational work | Lock collateral to prove you're honest | Cryptographically timestamp every transaction |
| **Security Model** | Financial suicide: Need 51% of global mining power + electricity | Financial suicide: Need $15B to buy 51% of stake + slashing | Computational suicide: Rewrite entire chain faster than honest network |
| **Energy Use** | 211 TWh/year (0.83% global) | ~0.01 TWh/year (0.005% of PoW) | ~0.009 TWh/year (0.004% of PoW) |
| **Consensus Speed** | 10 minutes per block | 12 seconds per block | 400 milliseconds per block |
| **TPS** | ~7 | ~15-30 | ~65,000+ |
| **How Cheating is Stopped** | Rewriting costs more than you'd gain | Losing your collateral (automatic slashing) | Computational impossibility (hashes don't match) |
| **Miner/Validator Count** | ~100K globally | 1M+ validators | ~800 quality validators |
| **Barrier to Entry** | High (need $M+ hardware + electricity) | Moderate (32 ETH = ~$100K) | Low (any amount SOL) |
| **Best For** | Store of value, immutability moat | Staking yields, DeFi ecosystem | Retail apps, real-time trading, payments |

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
| **PoW** | Security through computational cost (Bitcoin) |
| **PoS** | Security through economic collateral (Ethereum) |
| **PoH** | Security through cryptographic timestamps (Solana) |
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
| **Attestation** | Validator vote confirming a block is valid |
| **Block** | Bundle of transactions added to the chain |
| **Blockchain** | Distributed, immutable digital ledger |
| **Consensus** | How networks agree on truth |
| **Epoch** | Time period for validator duties (2-3 days on Solana) |
| **Finality** | When a transaction becomes irreversible |
| **Gas** | Transaction fee paid to validators |
| **Hash** | Cryptographic fingerprint of data |
| **Hashrate** | Measure of computing power in PoW |
| **Node** | Computer running blockchain software |
| **Nonce** | Number miners iterate to find valid hash |
| **Private Key** | Secret that proves ownership |
| **Public Key** | Address derived from private key |
| **Seed Phrase** | Words that can recover your keys |
| **Slashing** | Penalty for validator misbehavior |
| **Slot** | 400ms time window on Solana |
| **Stablecoin** | Token pegged to $1 USD |
| **Token** | Any digital asset on blockchain |
| **TPS** | Transactions Per Second |
| **Validator** | Node that creates new blocks |
| **VDF** | Verifiable Delay Function (core to PoH) |
| **Wallet** | Software holding your private keys |

---

**Last Updated:** January 16, 2026
**Version:** 2.0
