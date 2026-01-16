# DeFi Essentials: Staking, Swapping & Earning Yield

**Reading Time:** ~45 minutes
**Audience:** Users who understand crypto basics
**Level:** Intermediate
**Updated:** January 2026

---

## Table of Contents

1. [What You'll Learn](#what-youll-learn)
2. [Quick Acronym Reference](#quick-acronym-reference)
3. [Part 1: What is DeFi?](#part-1-what-is-defi)
   - [The Basic Idea](#the-basic-idea)
   - [Why DeFi Matters](#why-defi-matters)
   - [Smart Contracts: The Engine of DeFi](#smart-contracts-the-engine-of-defi)
4. [Part 2: Staking - Earn While Securing the Network](#part-2-staking---earn-while-securing-the-network)
   - [What is Staking?](#what-is-staking)
   - [How Staking Works on Solana](#how-staking-works-on-solana)
   - [Liquid Staking: Keep Your Liquidity](#liquid-staking-keep-your-liquidity)
5. [Part 3: Swapping Tokens](#part-3-swapping-tokens)
   - [How Swaps Work: AMMs](#how-swaps-work-amms)
   - [Slippage and Price Impact](#slippage-and-price-impact)
6. [Part 4: Providing Liquidity](#part-4-providing-liquidity)
   - [What is Liquidity Providing?](#what-is-liquidity-providing)
   - [Impermanent Loss: The Math](#impermanent-loss-the-math)
   - [Concentrated Liquidity](#concentrated-liquidity)
7. [Part 5: Types of Yield](#part-5-types-of-yield)
   - [1. Staking Yield](#1-staking-yield)
   - [2. Liquidity Provider (LP) Yield](#2-liquidity-provider-lp-yield)
   - [3. Lending Yield](#3-lending-yield)
   - [4. Concentrated Liquidity Yield](#4-concentrated-liquidity-yield)
   - [5. Protocol Token Rewards](#5-protocol-token-rewards)
   - [6. Composability Yield (Yield Farming)](#6-composability-yield-yield-farming)
8. [Part 6: Lending and Borrowing](#part-6-lending-and-borrowing)
   - [How Lending Protocols Work](#how-lending-protocols-work)
   - [Liquidation in Lending](#liquidation-in-lending)
   - [Liquidation Cascades](#liquidation-cascades)
9. [Part 7: Yield Metrics](#part-7-yield-metrics)
   - [APY vs APR](#apy-vs-apr)
   - [Effective Yield](#effective-yield)
10. [Part 8: Evaluating Opportunities](#part-8-evaluating-opportunities)
11. [Part 9: Getting Started Safely](#part-9-getting-started-safely)
12. [Summary](#summary)

---

## What You'll Learn

This document covers what you can actually do with crypto beyond holding it:
- What DeFi is and why it matters
- How to stake and earn passive income
- How token swapping works
- Six types of yield and how each works
- Risks to understand before participating (including detailed impermanent loss and liquidation mechanics)

By the end, you'll understand the main DeFi activities and how to evaluate opportunities.

---

## Quick Acronym Reference

| Acronym | What It Means |
|---------|---------------|
| **AMM** | Automated Market Maker |
| **APY** | Annual Percentage Yield |
| **APR** | Annual Percentage Rate |
| **DEX** | Decentralized Exchange |
| **IL** | Impermanent Loss |
| **LP** | Liquidity Provider |
| **LST** | Liquid Staking Token |
| **TVL** | Total Value Locked |

---

## Part 1: What is DeFi?

### The Basic Idea

**DeFi = Decentralized Finance**

Traditional finance uses banks as middlemen:
- Bank holds your savings
- Bank decides if you can borrow
- Bank takes fees and profits

DeFi uses code instead:
- Smart contracts hold assets
- Algorithms determine rates
- Fees go to users who provide liquidity

### Why DeFi Matters

**For users:**
- Higher yields (5-20% vs 0-4% at banks)
- No permission needed (anyone can participate)
- 24/7 access (no business hours)
- Full transparency (all transactions visible)

**Trade-offs:**
- You're responsible for security
- No customer support if you make mistakes
- Smart contract bugs can lose funds
- Yields aren't guaranteed

### Smart Contracts: The Engine of DeFi

A **smart contract** is a self-executing program on the blockchain that automatically enforces agreements when conditions are met. Code IS the contract—no lawyers, judges, or intermediaries needed. If condition X happens, then code does action Y automatically.

**Key difference from traditional software:**
- **Traditional software**: Code runs on a company's servers, can be changed/shut down anytime
- **Smart contracts**: Code runs on blockchain, **immutable once deployed**, cannot be deleted/changed (unless explicitly designed with upgrade mechanism)

**Real-world examples:**

*Example 1: Uniswap swap*
```
Condition: User sends 1 SOL
Then: Contract calculates USDC output using constant product formula
      Transfers USDC to user
      Transfers SOL to liquidity pool
      Updates pool reserves
Result: Atomic swap happens. No Uniswap employees involved.
```

*Example 2: Lending Protocol*
```
Condition: User deposits 100 SOL
Then: Contract records deposit in state
      Calculates accruing interest
      Allows borrowing against collateral
      Daily: Updates interest rates based on utilization
Result: Lending happens automatically. Interest accrues without human action.
```

**Why smart contracts matter for DeFi:**
- **No trust needed** (code enforces rules, not promises)
- **24/7 operation** (no business hours, no holidays)
- **Transparency** (everyone can read the code)
- **Atomic execution** (all-or-nothing; no partial fills or reversals)
- **No intermediary rent** (fees go to LPs/network, not bankers)

**The scary part (risks):**
- **Code is law...but code can be buggy** (Ronin bridge hack: $625M stolen because of access control bug)
- **Immutable = unchangeable forever** (if there's a bug, you can't just patch it; you have to deploy new contract)
- **Complexity = hidden risks** (a contract with 10K lines of code might have exploits nobody noticed)
- **Oracle manipulation** (if price feed is fake, contract makes bad decisions)

**Real disaster example:**
The DAO hack (2016): $50M stolen because of a reentrancy bug in the code. Smart contract did exactly what the code said—but the code had a flaw that let attackers drain funds.

**One-line mental model:**
A smart contract is **code that runs on the blockchain and automatically executes deals**. It's like a vending machine—you put in money, code verifies the transaction, dispenses the item—no human involved.

### DeFi on Solana

Solana's speed and low fees make DeFi practical:
- Transaction costs: ~$0.00025 (vs $2-50 on Ethereum)
- Confirmation time: ~400ms (vs 12+ seconds on Ethereum)
- This enables frequent transactions without fees eating profits

**Key DeFi platforms on Solana:**
- **Jupiter:** Best prices for swaps, recently launched Jupiter Lend (fastest-growing money market in DeFi history: $500M TVL in 24 hours)
- **Orca:** Concentrated liquidity pools and trading (pioneered "Whirlpools" on Solana)
- **Marinade:** Staking and liquid staking (3.1M+ directed stake TVL)
- **Raydium:** Community AMM with strong support

---

## Part 2: Staking - Earn While Securing the Network

### What is Staking?

When you stake, you lock up your tokens to help secure the blockchain. In return, you earn rewards.

**Think of it like:**
- A savings account that pays you for keeping money deposited
- But instead of a bank profit, rewards come from new tokens created by the network

### How Staking Works on Solana

1. **You delegate SOL to a validator**
   - Validators run the network infrastructure
   - You choose which validator to support
   - Your SOL stays in your control (non-custodial)

2. **Validator earns rewards**
   - For producing blocks honestly
   - Rewards come from network inflation + transaction fees

3. **You receive your share**
   - Minus validator commission (typically 5-8%)
   - Rewards distributed each epoch (~2-3 days)

### Staking Yields

| Network | Current APY | Minimum | Risk |
|---------|-------------|---------|------|
| **Solana** | 6-9% | Any amount | Slashing rare, protocol-backed |
| **Ethereum** | 3.2% | 32 ETH (~$100K) direct, any amount via pools | Very safe, mature protocol |

Solana offers higher yields because the network is younger and growing.

### Getting Started with Staking

**Direct staking:**
1. Open wallet that supports staking
2. Select "Stake" or "Delegate"
3. Choose a validator (consider commission rate, uptime)
4. Enter amount to stake
5. Confirm transaction

**Important:**
- Unstaking takes ~2-3 days (one epoch)
- Your SOL is locked during that period
- You keep full ownership (not custodial)

### Liquid Staking: Keep Your Liquidity

**Problem with regular staking:** Your tokens are locked. Can't use them for anything else.

**Solution:** Liquid Staking Tokens (LSTs)

**How it works:**
1. Deposit 10 SOL with a liquid staking protocol
2. Receive ~10 mSOL (Marinade's liquid staking token)
3. Your original SOL is staked (earning 6-9%)
4. Your mSOL can be used elsewhere (traded, used in DeFi)
5. mSOL value grows as staking rewards accumulate

**Popular LSTs on Solana:**
- **mSOL (Marinade):** Largest, most liquid, market leader in Solana liquid staking
- **JitoSOL (Jito):** Combines base staking rewards (6-9%) plus MEV rewards (1-3%), totaling 7-12% APY

**Why this matters:**
- Earn staking rewards AND keep liquidity
- Use LSTs as collateral for loans
- Provide liquidity in LST pools for extra yield

---

## Part 3: Swapping Tokens

### What is a Swap?

Exchanging one token for another directly on the blockchain.

**Example:**
- You have 1 SOL
- You want USDC
- You swap 1 SOL for ~150 USDC (depending on current price)

### How Swaps Work: AMMs

Traditional exchanges use order books (buyers and sellers post prices).

DeFi uses **Automated Market Makers (AMMs)**:
- Liquidity pools hold reserves of two tokens
- Mathematical formula determines price
- You trade against the pool, not another person

**The constant product formula:**
```
Token A amount × Token B amount = Constant
```

When you buy Token A, you add Token B to the pool. The ratio changes, adjusting the price.

### Using a DEX (Jupiter)

Jupiter is Solana's dominant DEX aggregator. It routes swaps across multiple liquidity pools to find best prices.

**To swap:**
1. Connect your wallet
2. Select tokens (what you have, what you want)
3. Enter amount
4. Review price and fees
5. Approve and sign transaction

**What to check:**
- **Price impact:** How much your trade moves the price
- **Slippage:** Maximum price change you'll accept
- **Fees:** Network fee + DEX fee (typically 0.3%)

### Slippage and Price Impact

**Slippage:** The difference between expected and actual price.

**Why it happens:**
- Prices change between when you click and when the transaction confirms
- Large orders move the market price

**Setting slippage tolerance:**
- 0.5%: Tight, might fail in volatile markets
- 1%: Standard for most swaps
- 3%+: Only for very volatile or illiquid tokens

**Price impact:** How much YOUR trade moves the price.
- 0.1%: Negligible
- 1%: Small
- 5%+: Significant (consider smaller trades)

---

## Part 4: Providing Liquidity

### What is Liquidity Providing?

You deposit tokens into a pool so others can swap against it. In return, you earn a share of swap fees.

**Example:**
- You deposit $1,000 SOL + $1,000 USDC
- Traders swap using your liquidity
- Pool charges 0.3% per swap
- You earn a portion of those fees based on your share of the pool

### How LP Rewards Work

**Detailed calculation:**
- You deposit $10K (5 SOL @ $1,000 + $5K USDC) into SOL/USDC pool on Orca
- Daily volume in pool: $10M
- Swap fee: 0.25%
- Daily fees collected: $10M × 0.25% = $25K
- Your share (if you're 0.1% of pool): $25 per day
- Annual yield: $25 × 365 = $9,125 per $10K = **91% APY**

**Critical disclaimer**: This assumes consistent $10M daily volume. Real-world volumes fluctuate. Also doesn't account for impermanent loss (IL). Realistic net APY after IL: 30-70%.

### Impermanent Loss: The Math

**Why it happens:**
An AMM **forces you to automatically sell high and buy low** as price moves (due to constant product formula), reducing final value compared to just holding the tokens.

**The math explained:**
An AMM like Uniswap keeps reserves balanced: `token_A × token_B = constant`. If you deposit equal value (e.g., 5 SOL + $5,000 USDC) and SOL price doubles:
- Without LP: You'd have 5 SOL + $5,000 USDC = $15,000 total (if SOL = $2,000)
- As LP: AMM forces you to sell SOL and buy USDC to rebalance → you end up with fewer SOL + more USDC = ~$14,142 total
- **Loss: ~$858** (the IL = 5.7%)

**IL grows with price divergence:**
- 1.5x price move = ~2% IL
- 2x move = ~5.7% IL
- 3x move = ~13.4% IL
- 4x move = ~20% IL

**Real example:**
- You deposit $10K (5 SOL @ $1,000 + 5K USDC) into SOL/USDC pool
- SOL price jumps to $1,200 (20% move)
- IL = ~0.64% = $64 loss
- But trading fees earned that month = $200
- **Net profit = $136** (fees overcome IL)

**When IL matters:**
- ✅ Stable pairs (USDC/USDT): IL negligible, fees dominate → good yields
- ❌ Volatile pairs (SOL/USDC): High IL risk → need 50%+ fees to compensate
- ✅ Correlated pairs (mSOL/SOL): Low IL → good risk/reward

**When it's "impermanent":**
If price returns to entry, IL goes to zero (you get your tokens back, minus any fees). But if you withdraw at peak divergence, IL becomes permanent.

**One-line mental model:**
Being an LP is a **short volatility trade**—you profit from stable prices + fees, but lose if volatility spikes. The bigger the move, the bigger you lose.

### Concentrated Liquidity

**Traditional LP:** Your liquidity spread across all possible prices ($0 to infinity).

**Concentrated LP:** You choose a specific price range.

**Example:**
- SOL trading at $150
- You provide liquidity only for $140-$160 range
- Higher capital efficiency = more fees per dollar

**Yield comparison:**
- Uniswap v2 full-range: 1x efficient
- Uniswap v3/Orca Whirlpools concentrated: 20-4000x efficient depending on range
- $100K in tight 1,800-2,200 SOL/USDC range can generate **200-400% APY** (vs 20-40% full-range)

**Trade-off:**
- If price exits your range, you earn zero fees until price returns
- IL concentrated into narrow range
- Requires monitoring and adjustment

---

## Part 5: Types of Yield

There are six main types of yield in DeFi. Understanding each helps you evaluate opportunities.

### 1. Staking Yield

Return earned by validators or delegators for securing the network.
- **Solana:** 6-9% APY
- **Ethereum:** 3.2% APY
- **Funded by:** Protocol inflation (newly created tokens) + transaction fees
- **Risk:** Slashing (losing stake for misbehavior), though rare for delegators

### 2. Liquidity Provider (LP) Yield

Return from trading fees earned by providing liquidity to AMM pools.

**Formula:** (trading fees earned per year / capital deployed) × 100

**Example calculation:**
- You deposit $10K into SOL/USDC pool
- Daily volume: $10M
- Swap fee: 0.25%
- Daily fees: $25K
- Your share (0.1% of pool): $25/day
- Annual: ~91% APY

**Reality:** Doesn't account for impermanent loss. Realistic net APY after IL: 30-70%.

### 3. Lending Yield

Return earned by depositing cryptocurrency into lending protocols.
- **Stablecoins:** 8-15% APY
- **Volatile assets:** Variable with demand
- **Risk:** Liquidation cascade (protocol insolvency from bad debt)

### 4. Concentrated Liquidity Yield

Advanced LP strategy providing liquidity only in specific price range.

**Example:** $100K in tight 1,800-2,200 SOL/USDC range can generate 200-400% APY (vs 20-40% full-range allocation).

**Risk:** IL concentrated into narrow range. If price moves outside range: you earn zero fees until price returns.

### 5. Protocol Token Rewards

New protocols incentivize users with governance tokens.

**Example:** Jupiter Lend launch offered 10% APY stablecoin interest + 50% APY JUP token rewards = 60% total APY.

**Risk:** Rewards token often crashes post-launch. 60% APY becomes 20% if token drops 60%.

### 6. Composability Yield (Yield Farming)

Combining multiple yield sources.

**Example strategy:**
- Deposit SOL → Receive mSOL (earn 6% staking)
- Deposit mSOL + SOL to Orca LP pool (earn 15% LP fees)
- Deposit LP tokens to lending protocol as collateral
- Borrow USDC against collateral (borrow 50% of value)
- Deploy USDC in Jupiter Lend (earn 10% lending yield)
- **Total blended yield:** 6% + 15% + 10% = 31% (simplified; actual calculation accounts for capital efficiency)

**Risks multiply:**
- Smart contract risk on 3+ protocols
- Impermanent loss on LP position
- Liquidation risk if borrowing
- More complexity = more can go wrong

---

## Part 6: Lending and Borrowing

### How Lending Protocols Work

You deposit assets, borrowers pay interest, you earn yield.

**How it works:**
1. Deposit USDC into lending protocol
2. Protocol lends to borrowers (who post collateral)
3. Borrowers pay interest
4. You receive share of interest payments

### Liquidation in Lending

When a borrower's collateral value falls below the minimum threshold, the protocol **forcibly closes the position and sells the collateral** to repay the debt.

**How it actually works (step by step):**

1. **You deposit collateral** (e.g., 100 SOL @ $100 = $10K)
2. **You borrow against it** (e.g., $5K USDC, leaving $5K buffer)
3. **Collateral value drops** (SOL falls to $90)
4. **Your position becomes risky** (collateral now $9K, debt $5K, buffer only $4K)
5. **Liquidators watch for this** (via smart contracts/bots)
6. **Liquidation triggered** (e.g., when buffer drops below 20%)
7. **Your SOL is sold** (all 100 SOL liquidated at ~$90 each = $9K)
8. **Debt is repaid** ($5K USDC returned to lenders)
9. **Liquidator takes cut** (e.g., $450 reward = 5% of collateral)
10. **You get leftovers** ($9K - $5K - $450 = $3,550 back, you lose $6,450)

**Real example (Jupiter Lend):**
- Deposit: 100 SOL ($10K @ $100)
- Borrow: $5,000 USDC against it
- Liquidation threshold: When your collateral drops below 120% of debt
  - Debt: $5,000
  - Min collateral needed: $5,000 × 1.2 = $6,000
- **Price drops to $60/SOL**
  - Your collateral: 100 SOL @ $60 = $6,000
  - **You're at liquidation threshold—liquidators will trigger**
- **Liquidation executes:**
  - Your 100 SOL sold for $6,000
  - Lenders repaid $5,000
  - Liquidator takes $300 (5%)
  - You get $700 back
  - **Loss: $9,300** (90%+ of original collateral gone)

**Why liquidation happens:**
- You're betting on price recovery, but price keeps falling
- Protocol needs to protect lenders (if SOL kept falling, lenders lose money)
- Incentive alignment: If you're underwater, liquidators profit by closing you out

**One-line mental model:**
Liquidation is the **protocol's kill switch** to protect lenders when your collateral can't cover your debt. It's not punishment—it's financial triage.

### Liquidation Cascades

If many people are liquidated at once:
1. Large liquidations create selling pressure
2. Price falls further
3. More positions hit liquidation threshold
4. More forced sales
5. Price crashes harder

**Real example:** Aug 2023 Solana flash crash → $2B in liquidations across Aave/Jupiter/Marinade in hours.

**How to avoid liquidation:**
- **Use low leverage** (borrow only 20-30% of collateral, not 80%)
- **Monitor health factor** (most protocols show a "health factor"; <1.5 = warning zone)
- **Use stop-loss** (close position before liquidation)
- **Diversify collateral** (don't put all in one volatile asset)

---

## Part 7: Yield Metrics

### APY vs APR

**APY (Annual Percentage Yield)**
Return including compounding interest. If yield is paid daily and reinvested, APY compounds.

**Formula:** APY = (1 + daily yield)^365 - 1

**Example:** 0.1% daily = (1.001)^365 - 1 = 44% APY (accounting for compounding)

**APR (Annual Percentage Rate)**
Return without compounding. Useful for comparing simple interest products.

**Example:** 10% APR stablecoin lending paid monthly = slightly less than 10% APY (no compounding)

### Effective Yield

Actual return after accounting for losses, fees, and variable factors.

**Effective yield of LP strategy:**
Gross fees earned - impermanent loss - protocol fees (typically 10-25% of gross fees)

Often **50-70% of advertised yield**.

### Yield Variability by Risk

| Yield Type | Risk Level | Typical APY | Safety |
|------------|-----------|-------------|--------|
| **Solana staking** | Low | 6-9% | Slashing rare, protocol-backed |
| **Ethereum staking** | Low | 3.2% | Very safe, mature protocol |
| **Stablecoin lending** | Medium | 8-15% | Liquidation risk if collateral drops |
| **Stablecoin LP** | Medium | 10-20% | Low IL |
| **Token LP (volatile pair)** | High | 30-100%+ | Impermanent loss can exceed yield |
| **New protocol rewards** | Very High | 50-500%+ | Token often crashes, liquidity risk |

---

## Part 8: Evaluating Opportunities

### Red Flags

**Too-good-to-be-true yields:**
- 100%+ APY on stablecoins? Unsustainable.
- Often funded by token emissions that will crash.

**New/unaudited protocols:**
- Smart contracts can have bugs
- Established protocols (Orca, Jupiter) have track records

**Token incentives replacing real yield:**
- APY paid in protocol tokens
- Token dumps → APY collapses
- Prefer fees from real activity

### Questions to Ask

1. **Where does the yield come from?**
   - Staking: network inflation
   - LP: trading fees
   - Lending: borrower interest
   - Token rewards: often unsustainable

2. **How long has this protocol existed?**
   - 2+ years with no exploits = good sign
   - New protocols = higher risk

3. **What are the risks?**
   - Smart contract bugs
   - Impermanent loss
   - Token price collapse
   - Liquidation

4. **Can I exit quickly?**
   - Liquid positions can be sold anytime
   - Staked positions have unlock periods
   - Low liquidity pools = can't exit without massive slippage

### Realistic Expectations

| Strategy | Advertised APY | Realistic APY | Why Different |
|----------|---------------|---------------|---------------|
| LP (volatile pair) | 100%+ | 30-50% | IL reduces returns |
| New protocol | 500%+ | 50% or loss | Token crashes |
| Staking | 6-9% | 6-9% | Sustainable |
| Stable LP | 10-20% | 10-20% | Low IL |

---

## Part 9: Getting Started Safely

### Start Small

**Don't:**
- Put all your savings into DeFi immediately
- Chase the highest yields
- Deposit into protocols you don't understand

**Do:**
- Start with 5-10% of your crypto holdings
- Use established protocols first
- Understand each step before proceeding

### Beginner Path

**Week 1-2:** Native staking
- Stake SOL directly
- Understand epochs and rewards
- Get comfortable with the process

**Week 3-4:** Liquid staking
- Try mSOL through Marinade
- Understand the LST concept
- See how mSOL can be used elsewhere

**Week 5-6:** Simple swaps
- Use Jupiter for token swaps
- Understand slippage and price impact
- Practice with small amounts

**Week 7-8:** LP (optional)
- Start with stable pairs (lower risk)
- Monitor impermanent loss
- Understand the mechanics

### Security Checklist

Before depositing into any DeFi protocol:

- [ ] Protocol has been audited by reputable firm
- [ ] Protocol has operated for 6+ months without exploits
- [ ] You understand where yield comes from
- [ ] You've tested with a small amount first
- [ ] You can afford to lose this money
- [ ] You've verified you're on the official website
- [ ] You understand how to exit the position

---

## Summary

| Activity | What It Is | Risk | Reward |
|----------|-----------|------|--------|
| **Staking** | Lock tokens to secure network | Low | 6-9% APY |
| **Liquid Staking** | Staking with liquidity | Low-Medium | 6-9% APY + flexibility |
| **Swapping** | Exchange one token for another | Low | N/A (utility) |
| **LP (Stable)** | Provide liquidity to pools | Medium | 10-20% APY |
| **LP (Volatile)** | Provide liquidity to volatile pairs | High | 15-50% APY |
| **Lending** | Deposit for borrowers to use | Medium | 8-15% APY |
| **Yield Farming** | Combine multiple yield sources | High | 20-50%+ APY |

---

## What's Next?

Now that you understand DeFi basics, the next document covers:
- **How trading and markets work**
- **Spot vs derivatives**
- **Leverage and liquidation risks**

Continue to: [04_TRADING_AND_MARKETS.md](./04_TRADING_AND_MARKETS.md)

---

## Quick Reference: DeFi Protocol Comparison

| Protocol | Type | TVL | Best For |
|----------|------|-----|----------|
| **Marinade** | Liquid Staking | $3B+ | Staking with liquidity |
| **Jito** | Liquid Staking + MEV | Growing | Maximum staking yield |
| **Jupiter** | Swap Aggregator + Lending | $500M+ (Lend) | Best swap prices, fast-growing lending |
| **Orca** | AMM/Concentrated Liquidity | $500M+ | Providing liquidity (Whirlpools) |
| **Raydium** | AMM/LP | $400M+ | Community pools |

---

**Last Updated:** January 16, 2026
**Version:** 2.0
