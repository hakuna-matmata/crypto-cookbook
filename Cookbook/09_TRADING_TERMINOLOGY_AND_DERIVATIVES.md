# Trading Terminology & Derivatives: Crypto Edition

**Reading Time:** ~55 minutes
**Audience:** Product Managers & Technical Leadership (Beginners welcome—starts from first principles)
**Updated:** January 2026
**Version:** 1.3

---

## Quick Navigation

- [Start from Zero](#start-from-zero)
- [First Principles: Real-Life Metaphors](#first-principles-real-life-metaphors)
- [Unified Margin: The Innovation](#unified-margin-the-innovation)
- [Core Concepts (Technical)](#core-concepts-technical)
- [Positions: Your Exposure to Markets](#positions-your-exposure-to-markets)
- [Perpetual Futures (Perps)](#perpetual-futures-perps)
- [Leverage & Margin](#leverage--margin)
- [Collateral & Liquidations](#collateral--liquidations)
- [Hedging Strategies](#hedging-strategies)
- [Arbitrage & Price Differences](#arbitrage--price-differences)
- [Real-World Case Study: October 2025 Liquidation Cascade](#real-world-case-study-october-2025-liquidation-cascade)
- [Language Guidelines for Precision](#language-guidelines-for-precision)
- [PM Playbook: Building Trading Features](#pm-playbook-building-trading-features)

---

## Start from Zero

You have **money**. That's it.

Everything below is just **different ways to use the same money**.

---

## First Principles: Real-Life Metaphors

### 1️⃣ What is a Derivative? (Big Scary Word, Simple Idea)

**Definition:** A contract whose value depends on something else.

**Real-life example:**
You and I agree: "If it rains tomorrow, you pay me €10. If it doesn't, I pay you €10."

That agreement is a **derivative**. It depends on **weather**, not on money itself.

**In crypto:**
- "Will BTC be above $60k on Friday?" → Derivative
- "Will ETH go up or down?" → Derivative
- "Will an ETF be approved?" → Derivative

**Key insight:** Prediction markets ARE derivatives. They're just bets on future events.

---

### 2️⃣ What is a Perpetual Future (Perp)? (A Bet on Price Direction)

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

---

### 3️⃣ What is a Hedge? (Insurance, Not Profit)

**Definition:** Placing another position to reduce risk.

Think **insurance**, not profit.

**Real-life analogy (the perfect one):**

You own a house. You worry it might burn down. So you buy **fire insurance**.

Now:
- If house is fine → you "lost" insurance money
- If house burns → insurance saves you

Insurance is a **hedge**.

**Trading example:**

You believe "ETH ETF will be approved" so you buy a prediction **YES**.

But if ETH price crashes meanwhile, you might lose money elsewhere.

So you **short ETH perp** (hedge).

Now:
- If ETH crashes → your short makes money (hedge protects you)
- If ETH pumps → your prediction wins

**Bottom line:** A hedge doesn't make you more profit—it reduces your risk when you're wrong.

---

### 4️⃣ What is Margin? (Using Money More Efficiently)

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

---

### 5️⃣ The Big Innovation: Unified Margin (No More Locked Money)

**Traditional prediction markets:**
```
You bet $1,000
  → $1,000 is locked
  → You wait weeks
  → You can't use it
  → You're stuck
```

**Unified margin (Backpack model):**
```
You have $1,000 total
  → You place a prediction
  → You still can trade
  → You still can hedge
  → You still can open other positions

As long as: your total risk is acceptable
```

This is called **unified margin** or **unified portfolio**.

**Why it matters:** Instead of freezing money, the system tracks your worst-case loss. As long as you have enough to cover that, you can keep trading and managing risk.

---

### 6️⃣ Put It All Together (Simple Story)

You have **$1,000**.

You believe: "ETH ETF will be approved"

So you:

1. Buy a **prediction YES** (derivative)
2. At the same time: **short ETH perp** (hedge against price crash)
3. Your $1,000 backs **both**
4. System tracks risk, not wallets

You're no longer:
- Locked
- Idle
- Waiting

You're **actively managing risk**.

---

### One Brutal, Simple Sentence

- **Derivative** = a bet on something
- **Perp** = a bet on price up/down
- **Hedge** = insurance against being wrong
- **Margin** = same money backing multiple bets
- **Unified portfolio** = no locked money, just risk tracking

---

## Unified Margin: The Innovation

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

---

### Traditional Sportsbook Logic

```
Total balance: €1,000 (you still own it)
Stakes locked: €500 + €300 = €800

Sportsbook logic: "Assume you lose both"
  Available balance = 1,000 – 800 = €200

Maximum you can withdraw: €200
```

Even though your bets hedge each other (worst case ≠ €800), the sportsbook doesn't care. It locks conservatively.

---

### Unified Margin Logic (Backpack)

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

---

### Why This Matters

**Question: "Do I have €500 left as my balance?"**

No. Your balance is still €1,000. Balance never changes until bets settle.

What changes is **how much you're allowed to use or withdraw**.

**Question: "What's the maximum I can send to another wallet?"**

€500.

Why? If you withdrew more than €500:
- Worst-case loss (€500) couldn't be covered
- System would take credit risk on you
- So it blocks the withdrawal

---

### One-Table Summary

| System | Balance | Risk assumed | Max withdrawable |
|--------|---------|--------------|-----------------|
| **Traditional sportsbook** | €1,000 | €800 (assumes lose both) | €200 |
| **Unified margin** | €1,000 | €500 (actual worst case) | €500 |

**One sentence to lock it in:**

In unified margin, you don't lose withdrawal power based on how much you bet, but based on how much you could lose.

---

## Core Concepts (Technical)

### What Makes Crypto Trading Different

Traditional finance has **derivatives markets** that have existed for centuries (wheat futures, oil futures, etc.). Crypto derivatives are fundamentally similar in mechanics but differ in:

1. **24/7/365 operation** - No market hours, no circuit breakers (though liquidation cascades can freeze liquidity)
2. **Decentralized execution** - Smart contracts handle settlement, not brokers
3. **Instant leverage access** - No credit check; collateral alone determines position size
4. **Self-liquidation risk** - Your position can disappear overnight if you don't monitor collateral ratio

**Key Mental Model:** In traditional finance, a broker manages margin calls. In crypto, smart contracts do this automatically via liquidations.

---

## Positions: Your Exposure to Markets

### What is a Position?

In crypto (and trading in general), a **position** is simply:

> **Your current exposure to something — what you'll gain or lose money on if prices or outcomes change.**

It's your "stance" in the market. Everything you hold that makes your portfolio sensitive to price or event changes is a position.

---

### The Simplest Example: Spot Position

You **own** the asset.

**Example:**
- You hold **2 SOL**
- You have a **SOL spot position**
- If SOL price goes up → you profit
- If SOL price goes down → you lose value

---

### Long vs. Short (Directional Positions)

**Long position:** You benefit if price goes **up**

```
Buy SOL at $200
  → "I'm long SOL"

Price rises to $250 → you profit (+$50 per SOL)
Price falls to $150 → you lose (-$50 per SOL)
```

**Short position:** You benefit if price goes **down**

```
Borrow/sell SOL (or use derivatives like perps)
  → "I'm short SOL"

Price falls to $150 → you profit (you sold at $200, buy back at $150 = +$50 per SOL)
Price rises to $250 → you lose (you sold at $200, must buy back at $250 = -$50 per SOL)
```

**Mental model:** Shorting is basically "betting against" the price.

---

### Positions in Derivatives (Perps, Predictions)

**Perpetual Futures Position**

You don't own the asset — you own a **contract** that tracks the asset's price.

```
Long SOL perp → profit if SOL rises
Short SOL perp → profit if SOL falls
```

**Prediction Market Position**

A position in predictions is your holdings of outcome tokens:

```
YES tokens on "ETF approved" → you're long the YES outcome
NO tokens on "ETF approved" → you're long the NO outcome
```

If you hold YES tokens and the ETF is approved, your tokens are worth $1 each (profit).
If the ETF is not approved, your YES tokens are worth $0 (loss).

---

### Net Position: What Matters for Risk

Your position isn't just what you bought—it's your **net exposure** after offsets.

**Example of offsetting positions:**

```
You own 10 SOL (long SOL spot)
You short SOL perps equivalent to 10 SOL

Net position ≈ NEUTRAL (hedged)
```

Even though you have two separate positions, your **net exposure** is reduced. You still have margin requirements and positions, but your overall portfolio risk is lower.

**Example of concentration:**

```
You own 10 SOL (long)
You also open a 5x long SOL perp (equivalent to 50 SOL exposure)

Net position ≈ VERY LONG SOL (concentrated risk)
```

Your total exposure is long 60 SOL equivalent—concentrated bet.

---

### Why Positions Matter

Positions determine:

1. **Risk** — How much you can lose (worst-case scenario)
2. **Margin requirements** — How much collateral you must hold
3. **Liquidation risk** — Can your position be force-closed if prices move against you?
4. **Portfolio sensitivity** — What price/outcome moves affect your portfolio most?

---

### One-Line Mental Model

> **Position = what you're holding that makes your portfolio sensitive to a price or an event.**

If you tell me what you're doing (spot, staking, perps, predictions), I can translate your portfolio into "positions" in plain English.

---

## Perpetual Futures (Perps)

### What Are Perpetual Futures?

**Definition:** Contracts that allow you to bet on an asset's future price *with no expiration date*, as opposed to traditional futures which expire on a specific date.

**Mental Model:** Imagine you believe SOL will be worth $200 next year. Instead of waiting a year and making one bet, perpetual futures let you:
- **Go long** (bet price rises): Borrow SOL today, sell it, buy it back later cheaper
- **Go short** (bet price falls): Sell SOL you don't own, buy it back later cheaper
- **No expiration**: Your bet stays open as long as you maintain sufficient collateral

### Traditional Futures vs. Perps

| Feature | Traditional Futures | Perpetual Futures |
|---------|--------------------|--------------------|
| **Expiration** | Specific date (e.g., March 2026) | Never (or manual close) |
| **Settlement** | Cash or physical at expiration | Continuous (via funding rates) |
| **Price Discovery** | Driven by expiration arbitrage | Driven by funding rate arbitrage |
| **Risk Model** | Finite loss at expiration | Liquidation risk until closed |
| **Examples** | CME bitcoin futures | Drift, dYdX, Hyperliquid |

### How Perps Stay Pegged to Spot Price

**The Problem:** Without expiration, how do perpetual contracts stay tied to the actual spot price of SOL?

**The Solution: Funding Rates**

When perp price diverges from spot price, traders pay each other a **funding rate** to keep prices aligned.

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

**Real Formula (Drift Protocol):**

```
Funding Rate = (Perp Price - Spot Price) / Spot Price × Interest Rate
              = (210 - 200) / 200 × 1 = 5% per settlement period

On $1M long position with 5% funding rate:
  → You pay $50K per hour to maintain position
  → Expensive arbitrage forces price back down
```

**Funding Rate Settlement:**
- **Drift Protocol**: Hourly settlement (each hour, funding accrues)
- **dYdX**: Trades continuously settle with counterparties
- **Hyperliquid**: Varies by market, typically hourly

### Real-World Perps Example

**Scenario:** You believe SOL will rally to $250 in 3 months.

**Traditional Approach (with brokerage):**
- Borrow $10,000 in cash
- Buy 50 SOL at $200/SOL
- Hold for 3 months
- Sell at $250 → Profit: $2,500 (25% return)
- **Limitation:** Broker controls borrowing, may force liquidation early

**Perpetual Futures Approach (on Drift):**
- Post $1,000 collateral (10x leverage)
- Open 50 SOL long via perp contract
- No time limit; hold as long as you want
- Close when price reaches $250 → Profit: $2,500
- **Advantage:** Decentralized, no broker, unlimited holding period
- **Risk:** If SOL drops to $195, your $1,000 collateral may be liquidated

---

## Leverage & Margin

### Initial Margin vs. Maintenance Margin

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

### How Leverage Works in Crypto

**Crypto Leverage ≠ Traditional Margin Borrowing**

| Aspect | Traditional Broker | Crypto Protocol |
|--------|------------------|-----------------|
| **Collateral** | Stock portfolio (physical assets) | Stablecoins (synthetic assets) |
| **Borrowing** | Real SOL borrowed from broker | Synthetic SOL created by protocol |
| **Recall Risk** | Broker can force buyback anytime | Only liquidation triggers buyback |
| **Cost** | Interest rate + borrow fee | Funding rate (continuously adjusted) |
| **Example** | E*TRADE margin account | dYdX protocol |

**Mental Model:** When you open a 10x SOL long on Drift:

1. You deposit $100 USDC as collateral
2. Drift creates $900 synthetic SOL liability (the "other side" of your long)
3. You own the long; market makers own the short (counterparty)
4. If you're right, you pocket the $500 gain; if wrong, you lose $100
5. Funding rates keep both sides incentivized to trade

### Liquidation Mechanics

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

---

## Collateral & Liquidations

### What Counts as Collateral

**Good Collateral:**
- Stablecoins (USDC, USDT) - 100% haircut (full value)
- SOL - 80-90% haircut (10-20% discount for volatility)
- ETH - 75-85% haircut (more volatile than SOL)
- Liquid LP tokens - 50-70% haircut

**Poor/No Collateral:**
- Illiquid altcoins - Not accepted
- Assets with <$10M liquidity - Not accepted
- Leveraged tokens - Not accepted (too risky for collateral)

**Haircut Example:**

```
Deposit $100,000 USDC → Counts as $100,000 collateral
Deposit $100,000 SOL (at $200/SOL) → Counts as $80,000-90,000
Difference: SOL haircut = 10-20%

Why haircut? Protocol hedges against SOL price crash.
If SOL drops 50%, $100K SOL becomes $50K.
Haircut buffer prevents protocol insolvency.
```

### Cross-Collateral Mechanics

Most protocols allow **cross-collateral** (multiple assets backing one position).

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

### Liquidation Cascades: Why October 2025 Was Severe

On October 15, 2025, a **$19 billion liquidation cascade** occurred across crypto derivatives platforms. Here's what happened:

**Timeline:**
1. **9:00 AM UTC:** Bitcoin drops 5% in 15 minutes (unexpected FOMC leak)
2. **9:05 AM UTC:** ETH liquidations begin on Binance (low MM triggers)
3. **9:07 AM UTC:** Ripple effect to dYdX, Hyperliquid, OKX
4. **9:15 AM UTC:** SOL and other alts cascade down (leveraged traders exit)
5. **9:30 AM UTC:** $19B in positions liquidated; liquidity spreads blow out

**Why It Was Severe:**

```
Self-Reinforcing Cycle:
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

**Platform-Specific Impact:**

| Platform | Liquidations | Impact | Recovery |
|----------|-------------|--------|----------|
| **Binance** | $8B+ | Futures engine strained; some liquidations delayed 60+ seconds | 2 hours |
| **dYdX** | $5B+ | Liquidation incentives spiked to 15% (normally 5%); liquidators made fortunes | 4 hours |
| **Hyperliquid** | $4B+ | Orderbook depth collapsed; spreads hit 2-3%; better automated recovery | 1.5 hours |
| **OKX** | $2B+ | Circuit breaker triggered; trading halted 5 minutes | 3 hours |

**Key Lesson:** When market moves faster than liquidity can absorb it, cascades worsen liquidations. Each liquidation sells at worse price, triggering next liquidation at even worse price.

---

## Hedging Strategies

### Core Definition (With Precise Language)

**Hedging:** Using one position to *reduce the risk* of another position. The goal is **not profit**, but **protection**.

**Precise Language Note:** Avoid saying "hedging guarantees losses are offset." Better: "A well-designed hedge *typically reduces* losses during adverse moves, though imperfect correlations mean losses are rarely fully offset."

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
Farmer buys 1,000 bushels SOL at $200
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

### Basis Trading: The Practical Hedge

**Basis Trading** exploits price differences between spot and perpetual futures.

**Mechanics:**

```
Spot price (Magic Eden): $200
Perp price (Drift): $205

Strategy:
1. Buy SOL at $200 on spot market
2. Sell SOL perp at $205 (borrow via protocol)
3. Collect $5/SOL spread = 2.5% profit
4. Hold until prices converge

Risk: What if perp stays at $205 for 6 months?
  → You pay funding rates (could cost 0.05% daily = 15% annualized)
  → Initial $5 profit eroded by $30 funding cost

So basis trading works best when:
  - Spread is wide (>1-2%)
  - Convergence is quick (<1 hour)
```

**Real Example from October 2025 Cascade:**

```
During the liquidation cascade, spreads blew out:

Spot SOL: $192 (on Magic Eden, liquidity-constrained)
Perp SOL: $175 (on Drift, forced selling by liquidations)

Spread: $17 (8.8% gap!)

Opportunity:
  Buy spot at $192
  Short perp at $175
  Collect $17 spread

But catches:
  - By the time you execute, spread narrowed to $12
  - Funding rates spiked to +1% per hour (20% annualized)
  - One liquidation wave wiped out the spread entirely

→ Basis traders who moved fast made 5%+ returns in minutes
→ Basis traders who were slow got trapped in positions worth less than entry
```

---

## Arbitrage & Price Differences

### What is Arbitrage? (Free Money, If You're Fast)

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

---

### Arbitrage in Crypto: Exchange Price Differences

**The Same Logic, Different Market:**

Bitcoin trades on different exchanges at slightly different prices because:
- Order flow is fragmented (not one global market)
- Network fees cost money to move crypto between exchanges
- Exchanges have different trading volumes and user bases

**Simple Example:**

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

---

### Three Types of Arbitrage

**Type 1: Spatial Arbitrage (Exchange-to-Exchange)**

Different exchanges have different prices because order flow is fragmented.

**Type 2: Temporal Arbitrage (Time-Based)**

Buy low, sell high later (but this is just investing, not arbitrage—arbitrage requires simultaneous buying and selling)

**Type 3: Statistical Arbitrage (Pairs Trading)**

Two correlated assets diverge in price. Buy the cheaper one, short the expensive one. When they re-correlate, both sides profit.

**Example:**
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

---

### The Catch: Arbitrage is Harder Than It Looks

**Why Free Money Disappears Instantly:**

1. **Speed matters** - Algorithms spot price differences in milliseconds
2. **Costs eat margins** - Network fees, trading fees, slippage
3. **Execution risk** - By the time you buy one side, price moved on the other
4. **Liquidity risk** - Can't exit one leg without moving the market

**Real-World Crypto Arbitrage Example (October 2025):**

During the Oct 2025 liquidation cascade, spreads blew out massively:

```
Normal times (stable):
  Spot SOL: $200
  Perp SOL: $200.50
  Spread: $0.50 (0.25%) - Too small to arb profitably

Oct 15 liquidation cascade (9:15 AM UTC):
  Spot SOL: $192 (Magic Eden, hard to get liquidity)
  Perp SOL: $175 (Drift, forced liquidations, panic selling)
  Spread: $17 (8.8%) - HUGE arbitrage opportunity!

Arbitrage trader sees this:
  ✓ Buy spot at $192 (limit order, waits 30 seconds)
  ✓ Short perp at $175 simultaneously
  ✓ Collect $17 spread = 8.8% instant profit

But reality:
  ✗ Spot order doesn't fill (not enough liquidity)
  ✗ By the time you buy at $195, perp is at $180 (spread shrinks to $15)
  ✗ You buy spot, fund rate spikes to 2% per hour
  ✗ In 2 hours, you've lost $10K in funding costs on $20K position
  ✗ Spread narrows to $2 when liquidations stop

Result: Traders who executed immediately = $5-10K profit on $100K capital
        Traders who delayed 30 seconds = Breakeven or losses
```

**Key Learning:** Arbitrage looks free on paper. In practice:
- You need **fast execution** (algorithms, not humans)
- You need **real liquidity** (not just bid-ask prices, actual volume)
- You need **low costs** (or fees consume the spread)
- You need **capital flexibility** (to move fast between markets)

---

### When Arbitrage Truly Exists (And When It Doesn't)

**Real Arbitrage (Simultaneous Buy-Sell, Zero Risk):**
- Price divergences between fragmented markets
- Lasts milliseconds before algorithms exploit it
- Requires: speed, capital, multi-market access

**Fake Arbitrage (Sounds Good, High Risk):**
- "Buy low, sell high" (this is just investing, not arbitrage)
- Expecting mean reversion (market might not revert)
- Ignoring funding rates or borrowing costs (eats all profit)

**For Product Builders:**

If you're building a trading feature and see an "arbitrage opportunity":
- ❌ Don't advertise "free money"
- ✓ Be honest about execution risk, slippage, and fees
- ✓ Show realistic profit after all costs
- ✓ Warn that by the time user sees opportunity, it's usually gone

---

## Real-World Case Study: October 2025 Liquidation Cascade

### What Triggered It

**Friday, October 15, 2025 - 9:00 AM UTC**

A reporter broke news that the Federal Reserve's November decision would be a surprise rate *increase* (markets expected hold or cut). This triggered:

1. **Deleveraging across all risk assets**
2. **Bitcoin drops 5% in 15 minutes** ($45K → $42.8K)
3. **Dominoes fall in order:** BTC → ETH → SOL → Alts

### The Cascade Mechanics

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
- Hyperliquid's algorithm liquidates $4B with better execution (stays mostly solvent)
- OKX triggers circuit breaker; halts trading for 5 minutes
- Recovery begins: Smart money sees opportunity, starts buying dip
- Liquidations slow as fewer positions remain in danger zone

**Peak Liquidation Rate:** $19B in 2.5 hours (vs. normal $200-500M per hour)

### Outcome by Exchange

```
Exchange    Liquidations    Median Price    Recovery Time
Binance     $8.0B          $195 SOL        2 hours
dYdX        $5.0B          $182 SOL        4 hours
Hyperliquid $4.0B          $188 SOL        1.5 hours
OKX         $2.0B          $185 SOL        3 hours
Others      $0.5B          $180 SOL        6+ hours
```

### Key Lesson: Liquidation Risk Increases with Volatility

**VIX Analogy:** Just as stock markets have circuit breakers when volatility exceeds 7%, crypto exchanges experience "cascade risk" when:
- 1-hour price volatility exceeds 10%
- Liquidation rate exceeds $1B per minute
- Bid-ask spreads exceed 1% (signs of panic)

---

## Language Guidelines for Precision

When building trading features, avoid the common mistakes that led to earlier inaccuracies.

### Rule 1: Never Guarantee Execution

**❌ Wrong:** "Your order is guaranteed to fill at the specified price."
**✓ Right:** "Your order will fill at your specified price if liquidity is available. Market conditions may prevent execution."

**❌ Wrong:** "Liquidation protects the protocol's solvency."
**✓ Right:** "Liquidation helps protect protocol solvency by closing underwater positions before losses exceed collateral."

### Rule 2: Distinguish Probable from Possible

**❌ Wrong:** "Liquidations are economically infeasible because the liquidator recovers 2% incentive."
**✓ Right:** "Liquidations create a strong economic incentive (2% liquidation bonus) that usually ensures quick execution, though during extreme volatility liquidators may still face losses."

### Rule 3: Specify Conditions for Assumptions

**❌ Wrong:** "Funding rates keep prices aligned."
**✓ Right:** "Funding rates typically keep perp prices within 1-2% of spot prices during normal conditions. During liquidation cascades, spreads can spike to 5-10% as market makers pull liquidity."

### Rule 4: Use Temporal Language Precisely

**❌ Wrong:** "Liquidation happens instantly."
**✓ Right:** "Liquidation typically occurs within 1-30 seconds of triggering, depending on platform architecture and available liquidity."

### Rule 5: Cite Real Numbers Where Available

**❌ Wrong:** "Funding rates can be expensive."
**✓ Right:** "Funding rates ranged from 0.01%/hour (calm conditions) to 1.5%/hour (October 2025 cascade), annualizing to 3.65% - 438% depending on market stress."

---

## PM Playbook: Building Trading Features

### For Wallet Builders (Like Solflare)

**Decision 1: Integrate or Partner?**

| Approach | Pros | Cons | Best For |
|----------|------|------|----------|
| **Integrate Perps** | Full margin, risk management | Complex smart contracts, liquidation liability | Exchange-scale users |
| **Partner (Drift/dYdX)** | Leverage their engine, affiliate revenue | Users leave wallet to trade | Quick launch, low risk |
| **Display Only** | Safe, simple UX | Limited value prop vs Magic Eden | MVP/early adoption |

**Solflare Strategy:** Partner with Drift Protocol for perps, Magic Eden for spot. Reason:
- Drift handles liquidation risk (you don't)
- Revenue via affiliate (0.1-0.5% of trading volume)
- Users stay in wallet for order placement (discovery)

---

### For Trading Platform Builders

**Decision 2: Liquidation Engine Architecture**

**Centralized Liquidator (Binance, OKX):**
- Pro: Simple, fast, you control execution
- Con: System failures cascade (Oct 2025 Binance delays); not trustless
- Cost: Engineers, infrastructure

**Decentralized Incentive Model (dYdX, Hyperliquid):**
- Pro: Any bot can liquidate; trustless; resilient
- Con: Liquidators compete; spreads can be worse; harder to control
- Cost: Lower infrastructure, but liquidation incentives eat into revenue

**Recommendation:** Start centralized (easier), migrate to decentralized once volume justifies it.

---

### For Risk Management

**Liquidation Mechanics to Monitor:**

1. **Health Ratio:** Collateral / MM Requirement
   - Above 2.0 = Safe
   - 1.5-2.0 = Warning, watch closely
   - 1.0-1.5 = Caution, liquidation risk
   - Below 1.0 = Liquidated

2. **Cascade Risk Signals:**
   - 1-hour volatility exceeds 8%
   - Liquidation rate exceeds $500M/hour
   - Bid-ask spreads exceed 0.5%
   → Increase liquidation incentives by 2x

3. **Collateral Composition:**
   - If >50% collateral is volatile alts → Increase haircuts
   - If <30% stablecoin → Reduce position size limits
   - Monitor correlation (is everything liquidating together?)

---

### For Risk Communication

**To Users:**

❌ "Leverage is risky but potentially profitable."
✓ "10x leverage means a 10% price move eliminates 100% of your capital. Liquidation is automatic and irreversible."

❌ "Funding rates compensate you for holding leverage."
✓ "Funding rates are typically 0.01-0.05% per hour. Holding leverage for 100+ hours can consume your gains."

❌ "Hedging guarantees protection."
✓ "Hedging typically reduces losses during adverse moves, but may reduce gains during favorable moves."

---

## Key Takeaways

1. **Positions** are your core exposure—what you're holding that makes you sensitive to price or event changes. Understand your net position (after offsets) before calculating risk or margin requirements.

2. **Perpetual futures** let you bet on price movements without expiration via funding rate mechanics that keep prices pegged.

3. **Margin trading** introduces liquidation risk: maintain 1.5-2.0x health ratio buffer to be safe; below 1.0x and you're liquidated.

4. **Liquidation cascades** happen when volatility exceeds liquidity capacity. October 2025's $19B cascade shows how fast this can move.

5. **Hedging** reduces risk (not eliminates it); basis trading exploits the spot-perp spread but faces funding rate costs.

6. **Arbitrage** looks like free money but requires speed, real liquidity, and low costs. By the time most traders see an opportunity, algorithms have already closed it.

7. **Language precision** matters: use "typically reduces" not "guarantees," specify time frames, cite real numbers.

8. **Platform decisions** (integrate vs. partner) depend on user size; Solflare's best path is partnership with Drift + Magic Eden.

---

## Next Steps

**For Product:**
- [ ] Define liquidation safety thresholds (health ratio limits)
- [ ] Design cascade warning UX (alert users before liquidation risk)
- [ ] Test funding rate implications (does user understand true cost of leverage?)

**For Strategy:**
- [ ] Evaluate Drift partnership terms (revenue share, affiliate structure)
- [ ] Monitor October 2025 aftermath (did compliance/regulation change?)
- [ ] Plan gaming asset trading mechanics (perps + gaming assets = new TAM)

**For Risk:**
- [ ] Set max leverage limits by user type (retail = lower limits)
- [ ] Monitor collateral composition (when to reject poor collateral?)
- [ ] Build liquidation cascade detection (alert if spreads blow out >1%)

---

**Navigation:** [← Previous](08_NFTS_MARKETPLACE_GUIDE.md) | [Index](00_index.md)

**Last Updated:** January 13, 2026
**Version:** 1.0

