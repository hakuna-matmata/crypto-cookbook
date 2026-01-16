# DeFi Essentials: Staking, Swapping & Earning Yield

**Reading Time:** ~30 minutes
**Audience:** Users who understand crypto basics
**Level:** Intermediate
**Updated:** January 2026

---

## What You'll Learn

This document covers what you can actually do with crypto beyond holding it:
- What DeFi is and why it matters
- How to stake and earn passive income
- How token swapping works
- Ways to earn yield on your assets
- Risks to understand before participating

By the end, you'll understand the main DeFi activities and how to evaluate opportunities.

---

## Quick Acronym Reference

| Acronym | What It Means |
|---------|---------------|
| **AMM** | Automated Market Maker |
| **APY** | Annual Percentage Yield |
| **DEX** | Decentralized Exchange |
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

### DeFi on Solana

Solana's speed and low fees make DeFi practical:
- Transaction costs: ~$0.00025 (vs $2-50 on Ethereum)
- Confirmation time: ~400ms (vs 12+ seconds on Ethereum)
- This enables frequent transactions without fees eating profits

**Key DeFi platforms on Solana:**
- **Jupiter:** Best prices for swaps
- **Orca:** Liquidity pools and trading
- **Marinade:** Staking and liquid staking
- **Raydium:** Community AMM

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

| Network | Current APY | Minimum |
|---------|-------------|---------|
| **Solana** | 6-9% | Any amount |
| **Ethereum** | 3.2% | 32 ETH (~$100K) direct, any amount via pools |

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
- **mSOL (Marinade):** Largest, most liquid
- **JitoSOL (Jito):** Includes MEV rewards (higher yields)

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

Jupiter is Solana's main swap aggregator. It finds the best prices across all pools.

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

**Basic math:**
- Pool has $10M total liquidity
- You contributed $2,000 (0.02% of pool)
- Pool does $1M in daily swaps
- Fees collected: $1M × 0.3% = $3,000
- Your daily share: $3,000 × 0.02% = $0.60
- Annual (if sustained): $219 on $2,000 = 11% APY

**Reality check:** Volumes fluctuate. Bull markets = high volume = high fees. Bear markets = opposite.

### The Risk: Impermanent Loss

**Problem:** When token prices change, you end up with different amounts than you deposited.

**Example:**
- Deposit: 10 SOL ($1,000) + 1,000 USDC ($1,000) = $2,000 total
- SOL doubles to $200
- Pool rebalances: you now have 7.07 SOL + 1,414 USDC
- Value: 7.07 × $200 + $1,414 = $2,828
- If you just held: 10 × $200 + $1,000 = $3,000
- **Loss: $172 (5.7% impermanent loss)**

**Why it's called "impermanent":**
- If SOL returns to $100, you get your original ratio back
- Loss only becomes permanent if you withdraw while prices diverged

**When LP makes sense:**
- Stable pairs (USDC/USDT): Almost no impermanent loss
- Correlated pairs (mSOL/SOL): Low impermanent loss
- High-volume pairs: Fees can exceed impermanent loss

### Concentrated Liquidity

**Traditional LP:** Your liquidity spread across all possible prices ($0 to infinity).

**Concentrated LP:** You choose a specific price range.

**Example:**
- SOL trading at $150
- You provide liquidity only for $140-$160 range
- Higher capital efficiency = more fees per dollar

**Trade-off:**
- If price exits your range, you earn zero fees
- Requires monitoring and adjustment

---

## Part 5: Ways to Earn Yield

### Yield Comparison

| Strategy | Typical APY | Risk Level | Effort |
|----------|-------------|------------|--------|
| **Native Staking** | 6-9% | Low | Low |
| **Liquid Staking** | 6-9% | Low-Medium | Low |
| **Stablecoin LP** | 10-20% | Medium | Low |
| **Major Pair LP** | 15-30% | Medium-High | Medium |
| **Lending** | 8-15% | Medium | Low |

### Lending Protocols

You deposit assets, borrowers pay interest, you earn yield.

**How it works:**
1. Deposit USDC into lending protocol
2. Protocol lends to borrowers (who post collateral)
3. Borrowers pay interest
4. You receive share of interest payments

**Current yields (January 2026):**
- Stablecoins: 8-15% APY
- SOL: 5-10% APY (varies with demand)

**Risk:** If borrowers get liquidated and collateral isn't sufficient, lenders can lose funds.

### Combining Strategies (Yield Stacking)

**Example with $10,000:**

**Layer 1:** Stake with Marinade
- Deposit 100 SOL → receive 100 mSOL
- Earn ~7% staking yield = $700/year

**Layer 2:** LP with mSOL
- Deposit 50 mSOL + 50 SOL into mSOL/SOL pool
- Earn ~15% LP fees = $750/year (on half)

**Layer 3:** Lend remaining
- Deposit 50 mSOL into lending protocol
- Earn ~10% lending yield = $500/year (on half)

**Total:** $700 + $750 + $500 = $1,950 on $10,000 = **~20% blended APY**

**Risks multiply:**
- Smart contract risk on 3 protocols
- Impermanent loss on LP position
- Liquidation risk if borrowing
- More complexity = more can go wrong

---

## Part 6: Evaluating Opportunities

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

## Part 7: Getting Started Safely

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

## Part 8: Common Mistakes to Avoid

### Chasing High APYs

**Problem:** New protocols offer 500%+ APY
**Reality:** Funded by token emissions, crashes within weeks
**Solution:** Focus on sustainable yield from real activity

### Not Understanding Impermanent Loss

**Problem:** "I provided liquidity but lost money"
**Reality:** IL can exceed LP fees in volatile markets
**Solution:** Start with stable pairs, understand the math

### Ignoring Gas Costs

**Problem:** On Ethereum, each transaction costs $5-50
**Reality:** Small positions lose money to fees
**Solution:** Use Solana or batch transactions

### Not Setting Slippage Properly

**Problem:** Transaction fails repeatedly
**Reality:** Slippage too tight for market conditions
**Solution:** Increase slippage for volatile tokens

### Connecting to Fake Sites

**Problem:** Clicked link in Discord, lost all funds
**Reality:** Phishing sites look identical to real ones
**Solution:** Always bookmark official URLs, verify manually

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
| **Jupiter** | Swap Aggregator | N/A | Best swap prices |
| **Orca** | AMM/LP | $500M+ | Providing liquidity |
| **Raydium** | AMM/LP | $400M+ | Community pools |

---

**Last Updated:** January 16, 2026
**Version:** 2.0
