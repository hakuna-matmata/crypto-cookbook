# Trading & Markets: Spot, Derivatives & Risk

**Reading Time:** ~55 minutes
**Audience:** Users who understand DeFi basics
**Level:** Intermediate to Advanced
**Updated:** January 2026

---

## Table of Contents

1. [What You'll Learn](#what-youll-learn)
2. [Quick Acronym Reference](#quick-acronym-reference)
3. [First Principles: Real-Life Metaphors](#first-principles-real-life-metaphors)
   - [What is a Derivative?](#1%EF%B8%8F%E2%83%A3-what-is-a-derivative)
   - [What is a Perpetual Future?](#2%EF%B8%8F%E2%83%A3-what-is-a-perpetual-future-perp)
   - [What is a Hedge?](#3%EF%B8%8F%E2%83%A3-what-is-a-hedge)
   - [What is Margin?](#4%EF%B8%8F%E2%83%A3-what-is-margin)
4. [Part 1: Spot Trading](#part-1-spot-trading)
   - [Order Types](#order-types)
   - [Key Concepts](#key-concepts)
5. [Part 2: Positions and Exposure](#part-2-positions-and-exposure)
   - [Long vs Short](#long-vs-short)
   - [Net Position](#net-position)
6. [Part 3: Derivatives - Betting on Price](#part-3-derivatives---betting-on-price)
   - [Perpetual Futures (Perps)](#perpetual-futures-perps)
   - [Funding Rates: Keeping Prices Aligned](#funding-rates-keeping-prices-aligned)
7. [Part 4: Leverage & Margin](#part-4-leverage--margin)
   - [How Leverage Works](#how-leverage-works)
   - [Initial Margin vs Maintenance Margin](#initial-margin-vs-maintenance-margin)
   - [Collateral and Haircuts](#collateral-and-haircuts)
8. [Part 5: Unified Margin - The Innovation](#part-5-unified-margin---the-innovation)
9. [Part 6: Liquidation](#part-6-liquidation)
   - [How Liquidation Works](#how-liquidation-works)
   - [Liquidation Cascades](#liquidation-cascades)
   - [October 2025 Case Study](#october-2025-case-study)
10. [Part 7: Hedging Strategies](#part-7-hedging-strategies)
    - [The Farmer Wheat Analogy](#the-farmer-wheat-analogy)
    - [Basis Trading](#basis-trading)
11. [Part 8: Arbitrage](#part-8-arbitrage)
    - [Types of Arbitrage](#types-of-arbitrage)
    - [The Catch: Why Arbitrage is Hard](#the-catch-why-arbitrage-is-hard)
12. [Part 9: CEX vs DEX Trading](#part-9-cex-vs-dex-trading)
13. [Part 10: Risk Management](#part-10-risk-management)
14. [Summary](#summary)

---

## What You'll Learn

This document covers how crypto trading works:
- Spot trading: buying and selling actual tokens
- Derivatives: betting on prices without owning assets
- Leverage: amplifying gains (and losses)
- Liquidation: how positions get force-closed
- Hedging and arbitrage strategies
- Risk management basics

By the end, you'll understand the mechanics of trading and the risks involved.

---

## Quick Acronym Reference

| Acronym | What It Means |
|---------|---------------|
| **CEX** | Centralized Exchange |
| **DEX** | Decentralized Exchange |
| **CLOB** | Central Limit Order Book |
| **Perp** | Perpetual Future |
| **IM** | Initial Margin |
| **MM** | Maintenance Margin |
| **OI** | Open Interest |

---

## First Principles: Real-Life Metaphors

Before diving into technical details, let's establish the core concepts using simple analogies.

### 1️⃣ What is a Derivative?

**Definition:** A contract whose value depends on something else.

**Real-life example:**
You and I agree: "If it rains tomorrow, you pay me €10. If it doesn't, I pay you €10."

That agreement is a **derivative**. It depends on **weather**, not on money itself.

**In crypto:**
- "Will BTC be above $60k on Friday?" → Derivative
- "Will ETH go up or down?" → Derivative
- "Will an ETF be approved?" → Derivative

**Key insight:** Prediction markets ARE derivatives. They're just bets on future events.

### 2️⃣ What is a Perpetual Future (Perp)?

A **perp** is just a **bet on price direction**. You're saying:
- "I think price will go up" → **Long**
- "I think price will go down" → **Short**

**Important:** You do NOT own the asset. You're just betting on price movement.

**Simple example:**
```
BTC = $50,000

You go long BTC perp:
  BTC → $55,000 → You win
  BTC → $45,000 → You lose

You never touched Bitcoin itself.
```

**Bottom line:** Perps = directional price bets, nothing more.

### 3️⃣ What is a Hedge?

**Definition:** Placing another position to reduce risk.

Think **insurance**, not profit.

**Real-life analogy:**
You own a house. You worry it might burn down. So you buy **fire insurance**.

Now:
- If house is fine → you "lost" insurance money
- If house burns → insurance saves you

Insurance is a **hedge**.

**Trading example:**
You believe "ETH ETF will be approved" so you buy a prediction **YES**. But if ETH price crashes meanwhile, you might lose money elsewhere. So you **short ETH perp** (hedge).

Now:
- If ETH crashes → your short makes money (hedge protects you)
- If ETH pumps → your prediction wins

**Bottom line:** A hedge doesn't make you more profit—it reduces your risk when you're wrong.

### 4️⃣ What is Margin?

**Definition:** Your money backs multiple things at once.

**Normal world (no margin):**
```
You have €1,000:
  • €500 in savings
  • €500 locked in a bet
  • Can't touch the locked €500
```

**Margin world:**
```
You have €1,000:
  • You place a €500 bet
  • But the €1,000 still backs your account
  • You can still trade (as long as total risk is safe)

Your money is NOT locked, just accounted for.
```

**Key difference:** In margin, your total money backs multiple positions. The money isn't frozen—just allocated to cover worst-case losses.

### One Brutal, Simple Sentence

- **Derivative** = a bet on something
- **Perp** = a bet on price up/down
- **Hedge** = insurance against being wrong
- **Margin** = same money backing multiple bets

---

## Part 1: Spot Trading

### What is Spot Trading?

**Spot trading = buying or selling actual tokens for immediate delivery.**

When you buy SOL on a spot market:
- You send USDC
- You receive actual SOL in your wallet
- You own the tokens

This is the simplest form of trading. No contracts, no borrowing, no leverage.

### Where Spot Trading Happens

**Centralized Exchanges (CEX):**
- Coinbase, Binance, Kraken
- Company holds your tokens
- Fast, liquid, traditional interface
- Requires account, identity verification

**Decentralized Exchanges (DEX):**
- Jupiter, Orca, Raydium
- You control your tokens (self-custody)
- Trade directly from your wallet
- No account required

### Order Types

**Market Order**
- "Buy/sell now at the best available price"
- Executes immediately
- May experience slippage in volatile markets

**Limit Order**
- "Buy/sell only if price reaches X"
- Waits until price hits your target
- May never execute if price doesn't reach limit

**Example:**
```
SOL currently trading at $150

Market buy: You get SOL at ~$150 (whatever's available)
Limit buy at $145: Order waits until SOL drops to $145
```

### Key Concepts

**Bid-Ask Spread**
The difference between the highest buy price (bid) and lowest sell price (ask).
- CEXs: 0.01-0.1% (tight)
- AMMs: 0.3-1% (wider)
- Tight spreads indicate liquid markets

**Price Impact**
How much your trade moves the price. Large orders in thin liquidity cause large impact. 10% price impact means execution at 10% worse price than spot rate.

**Slippage**
The difference between expected and actual execution price.
- Set slippage tolerance to prevent bad executions
- Higher tolerance = more likely to fill, but worse price possible

---

## Part 2: Positions and Exposure

### What is a Position?

**A position is your exposure to price movements.**

If SOL price changes, does your portfolio value change? If yes, you have a SOL position.

It's your "stance" in the market. Everything you hold that makes your portfolio sensitive to price or event changes is a position.

### Long vs Short

**Long Position**
You benefit when price goes UP.

```
Buy 10 SOL at $150
  → SOL rises to $180 → You profit $300
  → SOL falls to $120 → You lose $300
```

**Short Position**
You benefit when price goes DOWN.

```
Short 10 SOL at $150 (via derivatives)
  → SOL falls to $120 → You profit $300
  → SOL rises to $180 → You lose $300
```

**Mental model:** Shorting is basically "betting against" the price.

### Net Position

Your real exposure after considering all positions.

```
Example:
- Long 10 SOL (spot)
- Short 5 SOL (derivatives)
- Net position: Long 5 SOL

You're only exposed to 5 SOL worth of price movement.
```

**Example of concentration:**
```
You own 10 SOL (long)
You also open a 5x long SOL perp (equivalent to 50 SOL exposure)

Net position ≈ VERY LONG SOL (concentrated risk)
```

Your total exposure is long 60 SOL equivalent—concentrated bet.

---

## Part 3: Derivatives - Betting on Price

### What is a Derivative?

**A derivative is a contract whose value depends on something else.**

Simple example:
- "If SOL is above $150 tomorrow, you pay me $10. If below, I pay you $10."
- That's a derivative. It "derives" value from SOL's price.

### Perpetual Futures (Perps)

The most common crypto derivative.

**Key features:**
- Bet on price direction (up or down)
- No expiration date (unlike traditional futures)
- Don't own the actual token
- Can use leverage

**Traditional Futures vs. Perps:**

| Feature | Traditional Futures | Perpetual Futures |
|---------|--------------------|--------------------|
| **Expiration** | Specific date (e.g., March 2026) | Never (or manual close) |
| **Settlement** | Cash or physical at expiration | Continuous (via funding rates) |
| **Price Discovery** | Driven by expiration arbitrage | Driven by funding rate arbitrage |
| **Risk Model** | Finite loss at expiration | Liquidation risk until closed |
| **Examples** | CME bitcoin futures | Drift, dYdX, Hyperliquid |

### Funding Rates: Keeping Prices Aligned

**Problem:** Without expiration, how do perp prices stay close to spot?

**Solution:** Funding rates.

When perp price diverges from spot:
- If perp > spot: Longs pay shorts
- If perp < spot: Shorts pay longs

**Mechanics (Drift Protocol Example):**
```
Scenario: Perp price = $210 (bullish)
         Spot price = $200 (reality)

Funding Rate: +0.05% per hour (annualizes to ~438%)
  → Long position holders pay shorts 0.05% hourly
  → This makes longs expensive, encouraging selling
  → Price pressure brings perp price back to $200

If perp price < spot (bearish):
  → Shorts pay longs instead
  → Encourages buying, price rises back to spot
```

**Funding Rate Formula:**
```
Funding Rate = (Perp Price - Spot Price) / Spot Price × Interest Rate
             = (210 - 200) / 200 × 1 = 5% per settlement period

On $1M long position with 5% funding rate:
  → You pay $50K per hour to maintain position
  → Expensive arbitrage forces price back down
```

**Funding Rate Settlement:**
- **Drift Protocol**: Hourly settlement
- **dYdX**: Continuous settlement
- **Hyperliquid**: Varies by market, typically hourly

**Practical impact:**
- Holding a perp position costs money (funding)
- In bullish markets, longs pay shorts
- In bearish markets, shorts pay longs
- Can range from 0.01% to 1%+ per 8 hours

---

## Part 4: Leverage & Margin

### How Leverage Works

**Leverage = controlling more with less.**

Instead of buying $10,000 worth of SOL with $10,000, you could:
- Use 5x leverage: Control $50,000 with $10,000
- Use 10x leverage: Control $100,000 with $10,000

```
Without leverage:
- Capital: $1,000
- Buy: $1,000 of SOL
- SOL rises 10%: You profit $100 (10% return)

With 5x leverage:
- Capital: $1,000
- Control: $5,000 of SOL
- SOL rises 10%: You profit $500 (50% return)
```

**The flip side:**
```
With 5x leverage:
- Capital: $1,000
- Control: $5,000 of SOL
- SOL falls 10%: You lose $500 (50% of your capital)
- SOL falls 20%: You lose $1,000 (100% of your capital)
```

### Leverage Risk Summary

| Leverage | Price Move to Lose Everything |
|----------|------------------------------|
| 2x | 50% |
| 5x | 20% |
| 10x | 10% |
| 20x | 5% |
| 50x | 2% |

Higher leverage = faster gains OR faster total loss.

### Initial Margin vs Maintenance Margin

These are the two pillars of leverage risk management.

**Initial Margin (IM):** The *minimum collateral* required to *open* a position.

```
Example (Drift Protocol):
- 1x leverage → IM = 100% (deposit $100 to trade $100)
- 5x leverage → IM = 20% (deposit $100 to trade $500)
- 10x leverage → IM = 10% (deposit $100 to trade $1,000)

Formula: IM Requirement = 1 / Leverage

To open a 10x long on $10,000:
  → Required IM = $10,000 / 10 = $1,000
```

**Maintenance Margin (MM):** The *minimum collateral* required to *keep* a position open. Falls below IM because of leverage math.

```
If IM = 20% for 5x leverage:
   MM = 10% (typical crypto standard: 50% of IM)

Scenario:
- Deposit: $100 (meets 20% IM)
- Trade: $500 long SOL
- SOL price drops 10% → Position loss: -$50
- Remaining collateral: $50
- MM requirement: $50 (10% of $500)

You're AT the MM threshold. One more 2% price move
liquidates you.

Formula: Liquidation Price = Entry Price × (1 - MM)
         = $200 × (1 - 0.10)
         = $180

At $180 SOL, your position is liquidated.
```

### Collateral and Haircuts

**What Counts as Collateral:**

| Asset | Haircut | Effective Value |
|-------|---------|-----------------|
| Stablecoins (USDC, USDT) | 0% | 100% of value |
| SOL | 10-20% | 80-90% of value |
| ETH | 15-25% | 75-85% of value |
| Liquid LP tokens | 30-50% | 50-70% of value |

**Haircut Example:**
```
Deposit $100,000 USDC → Counts as $100,000 collateral
Deposit $100,000 SOL (at $200/SOL) → Counts as $80,000-90,000

Difference: SOL haircut = 10-20%

Why haircut? Protocol hedges against SOL price crash.
If SOL drops 50%, $100K SOL becomes $50K.
Haircut buffer prevents protocol insolvency.
```

**Cross-Collateral:**
```
Your account:
- $50,000 USDC collateral (value: $50,000)
- $25,000 SOL collateral (value: $20,000 after 20% haircut)
- Total collateral available: $70,000

Your positions:
- 5x long $100,000 SOL (MM requirement: $10,000)
- 3x long $80,000 ETH (MM requirement: $8,000)
- Total MM needed: $18,000

Account health: $70,000 / $18,000 = 388% (very safe)
```

---

## Part 5: Unified Margin - The Innovation

### The Problem It Solves

Most systems lock money when you place a bet. But smart traders want to:
- Hedge their bets (reduce risk)
- Open multiple positions (diversify)
- Withdraw safely (manage liquidity)

Traditional systems don't allow this efficiently. Unified margin does.

### How It Works: The Sportsbook Example

**Setup:** You have €1,000. You place two bets simultaneously:
- Bet A: €500 on "Team A wins"
- Bet B: €300 on "Team A loses" (hedge)

**Three key numbers (people confuse these):**
1. **Total balance** – How much money you own
2. **Risk/exposure** – How much you could lose in worst case
3. **Available/withdrawable** – How much you're allowed to take out

### Traditional Sportsbook Logic

```
Total balance: €1,000 (you still own it)
Stakes locked: €500 + €300 = €800

Sportsbook logic: "Assume you lose both"
  Available balance = 1,000 – 800 = €200

Maximum you can withdraw: €200
```

Even though your bets hedge each other (worst case ≠ €800), the sportsbook doesn't care. It locks conservatively.

### Unified Margin Logic

**Key difference:** Unified margin looks at **worst-case loss**, not total stakes.

**Calculate worst case:**
```
If Team A wins:
  • Bet A wins → +€500
  • Bet B loses → –€300
  • Net: +€200

If Team A loses:
  • Bet A loses → –€500
  • Bet B wins → +€300
  • Net: –€200

Worst-case loss: €500 (not €800)
```

**Unified margin says:**
```
Total balance: €1,000
Worst-case risk: €500
Available/withdrawable = 1,000 – 500 = €500
```

### Summary Comparison

| System | Balance | Risk assumed | Max withdrawable |
|--------|---------|--------------|-----------------|
| **Traditional** | €1,000 | €800 (assumes lose both) | €200 |
| **Unified margin** | €1,000 | €500 (actual worst case) | €500 |

**One sentence:** In unified margin, you don't lose withdrawal power based on how much you bet, but based on how much you could lose.

---

## Part 6: Liquidation

### How Liquidation Works

**Liquidation = your position is forcibly closed because you can't cover potential losses.**

**Liquidation Trigger:** Account equity < Maintenance Margin requirement

```
Account equity = Collateral + P&L (unrealized loss)
MM Requirement = Position size × MM%

If Account Equity < MM Requirement → Liquidation

Example:
- Collateral: $1,000
- 10x long position (size: $10,000)
- MM requirement: $10,000 × 10% = $1,000
- Current SOL price: $195 (down 2.5% from $200 entry)
- Unrealized loss: -$250
- Account equity: $1,000 - $250 = $750
- $750 < $1,000 MM? → YES → LIQUIDATED
```

**What Happens When You're Liquidated:**

1. **Protocol liquidates your position** (sells your long or buys your short)
2. **Liquidation fee paid** (typically 5-10% of position, goes to protocol/liquidators)
3. **Remaining collateral returned** (if any survives fee)

**Example with Fees:**
```
Position liquidated at $195:
- Remaining equity: $750
- Liquidation fee (5%): -$500 (5% of $10K position)
- Final return: $250 (back to you)
- Total loss: $750 (vs $1,000 invested)
```

### Liquidation Cascades

**Self-Reinforcing Cycle:**
```
Spot price falls 5%
    ↓
Leveraged positions hit MM threshold
    ↓
Liquidations triggered (forced selling)
    ↓
Selling pressure deepens price decline
    ↓
More positions hit MM (cascading effect)
    ↓
Market makers pull bids (liquidity dries up)
    ↓
Prices fall faster than can be liquidated
    ↓
Some positions liquidate at terrible prices
```

### October 2025 Case Study

**Friday, October 15, 2025 - 9:00 AM UTC**

A reporter broke news that the Federal Reserve's November decision would be a surprise rate *increase* (markets expected hold or cut). This triggered:

1. **Deleveraging across all risk assets**
2. **Bitcoin drops 5% in 15 minutes** ($45K → $42.8K)
3. **Dominoes fall in order:** BTC → ETH → SOL → Alts

**Timeline:**

**Hour 1 (9:00-10:00 AM UTC):**
- Binance futures engine sees 3% of positions at liquidation risk
- Liquidations triggered: $500M in 5 minutes
- This selling pressure pushes BTC to $41.5K (10% down from before news)
- All altcoins follow (SOL: $198 → $185)

**Hour 2 (10:00-11:00 AM UTC):**
- dYdX detects 8% of positions at liquidation risk
- Liquidation engine activates; liquidators see 10%+ liquidation incentives (normally 2-5%)
- $8B liquidated as traders race to get filled
- Spreads blow out (normal: 5 bps; now: 50-200 bps)
- Market makers pull liquidity (because losses are too large)

**Hour 3 (11:00-12:00 PM UTC):**
- Hyperliquid's algorithm liquidates $4B with better execution
- OKX triggers circuit breaker; halts trading for 5 minutes
- Recovery begins: Smart money sees opportunity, starts buying dip
- Liquidations slow as fewer positions remain in danger zone

**Peak Liquidation Rate:** $19B in 2.5 hours (vs. normal $200-500M per hour)

**Outcome by Platform:**

| Platform | Liquidations | Impact | Recovery Time |
|----------|-------------|--------|---------------|
| **Binance** | $8B+ | Futures engine strained; some liquidations delayed 60+ seconds | 2 hours |
| **dYdX** | $5B+ | Liquidation incentives spiked to 15% (normally 5%); liquidators made fortunes | 4 hours |
| **Hyperliquid** | $4B+ | Orderbook depth collapsed; spreads hit 2-3%; better automated recovery | 1.5 hours |
| **OKX** | $2B+ | Circuit breaker triggered; trading halted 5 minutes | 3 hours |

**Key Lesson:** When market moves faster than liquidity can absorb it, cascades worsen liquidations. Each liquidation sells at worse price, triggering next liquidation at even worse price.

---

## Part 7: Hedging Strategies

### Core Definition

**Hedging:** Using one position to *reduce the risk* of another position. The goal is **not profit**, but **protection**.

**Precise Language:** Avoid saying "hedging guarantees losses are offset." Better: "A well-designed hedge *typically reduces* losses during adverse moves, though imperfect correlations mean losses are rarely fully offset."

### The Farmer Wheat Analogy

A wheat farmer plants 10,000 bushels in spring:

**Unhedged Risk:**
- Plant in April (unknown harvest price)
- Harvest in September at spot price
- If wheat price crashes → Income drops 50%
- **Outcome:** High profit in bull markets; catastrophic loss in bear markets

**Hedged Approach:**
- Plant in April
- Simultaneously sell wheat futures for September delivery at locked-in price
- Harvest in September; deliver wheat via futures contract
- **Outcome:** Stable, predictable income regardless of price moves
- **Cost:** Opportunity cost—if price rallies, farmer doesn't benefit

**In Crypto:**
```
Farmer buys 1,000 SOL at $200
  Upside: Sells at $300 → +50% gain
  Downside: Price crashes to $100 → -50% loss

Farmer shorts 1,000 SOL on perps (hedge)
  Long spot: Up $100K if SOL → $300
  Short perp: Down $100K if SOL → $300
  Net: $0 (hedged, no profit/loss)

Real scenario: SOL → $250
  Long spot: +$50K
  Short perp: -$50K
  Net: ~$0 (minus funding costs)

Farmer paid ~$5K in funding rates to achieve this protection.
```

### Basis Trading

**Basis Trading** exploits price differences between spot and perpetual futures.

**Mechanics:**
```
Spot price (Magic Eden): $200
Perp price (Drift): $205

Strategy:
1. Buy SOL at $200 on spot market
2. Sell SOL perp at $205 (short via protocol)
3. Collect $5/SOL spread = 2.5% profit
4. Hold until prices converge

Risk: What if perp stays at $205 for 6 months?
  → You pay funding rates (could cost 0.05% daily = 15% annualized)
  → Initial $5 profit eroded by $30 funding cost

So basis trading works best when:
  - Spread is wide (>1-2%)
  - Convergence is quick (<1 hour)
```

**During October 2025 Cascade:**
```
Spreads blew out:
Spot SOL: $192 (on Magic Eden, liquidity-constrained)
Perp SOL: $175 (on Drift, forced selling by liquidations)

Spread: $17 (8.8% gap!)

Traders who executed immediately = $5-10K profit on $100K capital
Traders who delayed 30 seconds = Breakeven or losses
```

---

## Part 8: Arbitrage

### What is Arbitrage?

**Definition:** Buying something at one price and simultaneously selling it at a higher price, pocketing the difference with zero risk.

**Real-life example:**
You're at a farmers market. A farmer sells apples for €1/kg. Two blocks away, a restaurant buys apples for €1.50/kg.

You:
1. Buy 100 kg from farmer at €1 = €100
2. Sell to restaurant at €1.50 = €150
3. Pocket €50 profit
4. Zero risk (you sold before you paid)

That's arbitrage. It exists because:
- Different buyers/sellers don't know each other's prices
- Markets are inefficient
- Friction prevents instant alignment

### Types of Arbitrage

**Type 1: Spatial Arbitrage (Exchange-to-Exchange)**
Different exchanges have different prices because order flow is fragmented.

```
Binance Bitcoin: $65,000
Kraken Bitcoin: $65,100
Difference: $100 (0.15%)

Arbitrage opportunity:
1. Buy on Binance at $65,000 (cost: $6.5M + 0.1% fee = ~$6.515M)
2. Withdraw to Kraken (cost: $15 network fee)
3. Sell on Kraken at $65,100 (receive: $6.51M after 0.1% fee)
4. Profit: $6.51M - $6.515M - $15 = ~$500

BUT: By the time you buy, price likely moved. Arbitrage is faster than you.
```

**Type 2: Statistical Arbitrage (Pairs Trading)**
Two correlated assets diverge in price. Buy the cheaper one, short the expensive one.

```
Solana and Ethereum are correlated (both crypto, move together)
Normal ratio: SOL = 0.035 ETH
Today: SOL = 0.032 ETH (SOL dropped more than expected)

Strategy:
1. Buy 100 SOL at $200 = $20K
2. Short 3.5 ETH at $2,000 = $7K short
3. When ratio reverts: SOL rises to $220 and ETH stays $2,000
   - Long SOL: +$2,000
   - Short ETH: 0 P&L (they didn't move)
   - Net: +$2,000 profit (12% on capital)

Risk: Correlation breaks; they don't revert together.
```

### The Catch: Why Arbitrage is Hard

**Why Free Money Disappears Instantly:**

1. **Speed matters** - Algorithms spot price differences in milliseconds
2. **Costs eat margins** - Network fees, trading fees, slippage
3. **Execution risk** - By the time you buy one side, price moved on the other
4. **Liquidity risk** - Can't exit one leg without moving the market

**Real Arbitrage (Simultaneous Buy-Sell, Zero Risk):**
- Price divergences between fragmented markets
- Lasts milliseconds before algorithms exploit it
- Requires: speed, capital, multi-market access

**Fake Arbitrage (Sounds Good, High Risk):**
- "Buy low, sell high" (this is just investing, not arbitrage)
- Expecting mean reversion (market might not revert)
- Ignoring funding rates or borrowing costs (eats all profit)

---

## Part 9: CEX vs DEX Trading

### Centralized Exchanges (CEX)

**Pros:**
- Deep liquidity (tight spreads)
- Fast execution
- Advanced order types
- Fiat on/off ramps

**Cons:**
- Custodial (they hold your keys)
- Identity verification required
- Can freeze accounts
- Counterparty risk (exchange can fail)

**Examples:** Binance, Coinbase, Kraken

### Decentralized Exchanges (DEX)

**Pros:**
- Self-custody (you hold keys)
- No identity verification
- Permissionless access
- Transparent (on-chain)

**Cons:**
- Lower liquidity (higher slippage)
- Slower execution
- Limited order types
- Smart contract risk

**Examples:** Jupiter, Orca, Raydium, Drift

### When to Use Each

| Situation | Best Choice |
|-----------|-------------|
| Converting fiat to crypto | CEX |
| Large trades (>$100K) | CEX |
| Privacy matters | DEX |
| Want self-custody | DEX |
| Trading exotic tokens | DEX |
| Active day trading | CEX |

### Hybrid Approach

Many traders use both:
1. CEX for fiat on/off ramps
2. DEX for actual trading
3. Transfer to self-custody wallet for storage

---

## Part 10: Risk Management

### Position Sizing

**Rule of thumb:** Don't risk more than 5-10% of capital on a single trade.

```
Capital: $10,000
Max risk per trade: $500-1,000

If using 5x leverage:
- Position size: $2,500-5,000
- Potential loss limited to 10% of capital
```

### Stop Losses

**A stop loss automatically exits your position at a predetermined price.**

```
Buy SOL at $150
Set stop loss at $140

If SOL drops to $140:
- Position auto-closes
- You lose $10 per SOL
- Prevents further losses
```

### Health Ratio Monitoring

Monitor your account health ratio:
- **Above 2.0:** Safe
- **1.5-2.0:** Warning, watch closely
- **1.0-1.5:** Caution, liquidation risk
- **Below 1.0:** Liquidated

### Cascade Risk Signals

Be cautious when:
- 1-hour volatility exceeds 8%
- Liquidation rate exceeds $500M/hour
- Bid-ask spreads exceed 0.5%
- Funding rates are extremely high (>0.1% per 8h)
- Open interest growing faster than price

### Common Mistakes to Avoid

1. **Too Much Leverage:** 50x leverage feels like "more profit" but 2% move wipes you out. Start with 2-3x maximum.

2. **No Stop Loss:** "It will come back" is dangerous. Always set a stop loss before entering.

3. **Ignoring Funding Costs:** Holding leveraged position for weeks—funding eats all your profits. Calculate funding costs before entering.

4. **Trading Everything:** Trying to catch every move leads to fees and losses accumulating. Focus on high-conviction trades only.

---

## Summary

| Concept | Key Point |
|---------|-----------|
| **Spot Trading** | Buy/sell actual tokens |
| **Position** | Your exposure to price changes |
| **Long** | Profit when price goes up |
| **Short** | Profit when price goes down |
| **Perps** | Bet on price without owning asset |
| **Funding Rates** | Payments that keep perp prices aligned with spot |
| **Leverage** | Amplify gains AND losses |
| **Initial Margin** | Collateral to open position |
| **Maintenance Margin** | Collateral to keep position open |
| **Liquidation** | Position force-closed when margin insufficient |
| **Unified Margin** | Risk-based capital efficiency |
| **Hedging** | Reduce risk with offsetting position |
| **Arbitrage** | Profit from price differences (requires speed) |
| **Stop Loss** | Automatic exit at predetermined price |

---

## What's Next?

Now that you understand trading mechanics, the next document covers:
- **NFTs: what they are and how they work**
- **Marketplaces and trading NFTs**
- **Evaluating NFT opportunities**

Continue to: [05_NFTS_COMPLETE_GUIDE.md](./05_NFTS_COMPLETE_GUIDE.md)

---

## Quick Reference: Leverage vs Risk

| Leverage | Move to Double | Move to Lose All |
|----------|---------------|------------------|
| 1x (none) | 100% | -100% |
| 2x | 50% | -50% |
| 5x | 20% | -20% |
| 10x | 10% | -10% |
| 20x | 5% | -5% |

---

**Last Updated:** January 16, 2026
**Version:** 2.0
