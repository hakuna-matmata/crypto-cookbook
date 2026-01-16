# Trading & Markets: Spot, Derivatives & Risk

**Reading Time:** ~35 minutes
**Audience:** Users who understand DeFi basics
**Level:** Intermediate
**Updated:** January 2026

---

## What You'll Learn

This document covers how crypto trading works:
- Spot trading: buying and selling actual tokens
- Derivatives: betting on prices without owning assets
- Leverage: amplifying gains (and losses)
- Liquidation: how positions get force-closed
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
The difference between the highest buy price and lowest sell price.
- Tight spread (0.1%): Liquid market, low cost to trade
- Wide spread (2%+): Illiquid market, expensive to trade

**Price Impact**
How much your trade moves the price.
- Small trades: Negligible impact
- Large trades: Can move the market significantly

**Slippage**
The difference between expected and actual execution price.
- Set slippage tolerance to prevent bad executions
- Higher tolerance = more likely to fill, but worse price possible

---

## Part 2: Positions and Exposure

### What is a Position?

**A position is your exposure to price movements.**

If SOL price changes, does your portfolio value change? If yes, you have a SOL position.

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

Shorting requires borrowing or using derivatives (covered next).

### Net Position

Your real exposure after considering all positions.

```
Example:
- Long 10 SOL (spot)
- Short 5 SOL (derivatives)
- Net position: Long 5 SOL

You're only exposed to 5 SOL worth of price movement.
```

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

**How perps work:**
```
You believe SOL will rise.

Open a long SOL perp:
  - Entry price: $150
  - SOL rises to $180: You profit $30 per unit
  - SOL falls to $120: You lose $30 per unit

You never touch actual SOL. Just the price exposure.
```

### Funding Rates: Keeping Prices Aligned

**Problem:** Without expiration, how do perp prices stay close to spot?

**Solution:** Funding rates.

When perp price diverges from spot:
- If perp > spot: Longs pay shorts
- If perp < spot: Shorts pay longs

**Effect:** Creates pressure to bring prices back together.

**Practical impact:**
- Holding a perp position costs money (funding)
- In bullish markets, longs pay shorts
- In bearish markets, shorts pay longs
- Can range from 0.01% to 1%+ per 8 hours

---

## Part 4: Leverage

### What is Leverage?

**Leverage = controlling more with less.**

Instead of buying $10,000 worth of SOL with $10,000, you could:
- Use 5x leverage: Control $50,000 with $10,000
- Use 10x leverage: Control $100,000 with $10,000

### How Leverage Works

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

### Margin Requirements

**Initial Margin (IM):** How much you need to open a position.
```
10x leverage on $10,000 position:
IM = $10,000 / 10 = $1,000 required
```

**Maintenance Margin (MM):** How much you need to keep it open.
```
Typically 50% of IM.
For 10x position: MM = $500

If your account drops below $500, liquidation.
```

---

## Part 5: Liquidation

### What is Liquidation?

**Liquidation = your position is forcibly closed because you can't cover potential losses.**

When your collateral falls below the maintenance margin requirement, the system sells your position automatically.

### How Liquidation Works

```
Step by step:

1. Open position: 10x long SOL, $1,000 collateral
2. Position size: $10,000
3. Maintenance margin: $1,000 (10% of position)

4. SOL drops 5%:
   - Position loss: $500
   - Remaining collateral: $500
   - Still above MM? No. Liquidation triggered.

5. System sells your position at market price
6. Liquidation fee taken (typically 5%)
7. Remaining collateral returned (if any)
```

### The Liquidation Price

You can calculate where you'll be liquidated:

```
Formula (simplified):
Liquidation Price = Entry Price × (1 - 1/Leverage)

Example with 10x long at $150:
Liquidation = $150 × (1 - 1/10)
            = $150 × 0.9
            = $135

If SOL drops from $150 to $135 (-10%), you're liquidated.
```

### Liquidation Cascades

**What happens when many positions liquidate at once:**

1. Price drops unexpectedly
2. Leveraged longs hit liquidation threshold
3. Forced selling adds more downward pressure
4. Price drops further
5. More positions liquidate
6. Cascade accelerates

**Real example: October 2025**
- $19 billion liquidated in 24 hours
- Cascading liquidations amplified a 5% drop into 10%+
- Long positions: $16.7B liquidated
- Short positions: $2.5B liquidated

**Lesson:** During high volatility, liquidations can happen faster and worse than expected.

---

## Part 6: Hedging

### What is Hedging?

**Hedging = reducing risk by taking an offsetting position.**

It's insurance, not profit-seeking.

### Simple Hedge Example

```
Scenario: You own 10 SOL ($1,500). You're worried about a crash.

Hedge: Short 10 SOL via perps.

Now:
- If SOL falls 20%: Spot loses $300, Short gains $300 = Net $0
- If SOL rises 20%: Spot gains $300, Short loses $300 = Net $0

You're protected from the crash, but also don't benefit from the rise.
```

### When to Hedge

**Hedge makes sense when:**
- You hold tokens long-term but expect short-term volatility
- You want to lock in gains without selling
- You're in a risky position and want protection

**Hedge costs:**
- Funding rates on perp positions
- Opportunity cost if price moves favorably
- Transaction fees

---

## Part 7: CEX vs DEX Trading

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

**Examples:** Jupiter, Orca, Raydium

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

## Part 8: Risk Management

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

**Types:**
- Market stop: Exits at market price when triggered
- Limit stop: Exits at limit price or better

### Diversification

Don't put all capital in one trade or one asset.

```
Bad: $10,000 all in 10x long SOL
Good: $3,000 in SOL, $3,000 in ETH, $4,000 in stablecoins
```

### Emotional Discipline

Common mistakes to avoid:
- **Revenge trading:** Trying to recover losses immediately
- **FOMO:** Chasing pumps at the top
- **Overconfidence:** Increasing size after wins
- **Hope:** Holding losers too long

---

## Part 9: Trading Platforms on Solana

### Spot Trading

**Jupiter**
- Aggregator finding best prices across all DEXs
- Most used swap platform on Solana
- Simple interface for basic swaps

**Orca**
- Concentrated liquidity AMM
- Good for larger trades (less slippage)
- Clean user interface

**Raydium**
- Community-driven AMM
- Good for new tokens
- Launchpad integration

### Derivatives

**Drift Protocol**
- Native Solana perpetuals
- Up to 10x leverage
- Growing liquidity

**Hyperliquid**
- High-performance order book
- Sub-second execution
- Cross-chain support

---

## Part 10: Key Metrics to Watch

### For Spot Trading

| Metric | What It Tells You |
|--------|-------------------|
| **24h Volume** | How active the market is |
| **Liquidity Depth** | How much you can trade without moving price |
| **Bid-Ask Spread** | Cost of trading |
| **Price Chart** | Historical price movements |

### For Derivatives

| Metric | What It Tells You |
|--------|-------------------|
| **Open Interest** | Total value of outstanding contracts |
| **Funding Rate** | Cost to hold position, market sentiment |
| **Liquidation Map** | Where forced selling will happen |
| **Long/Short Ratio** | Market positioning |

### Warning Signs

**Be cautious when:**
- Funding rates are extremely high (>0.1% per 8h)
- Open interest growing faster than price
- Long/short ratio extremely skewed
- Bid-ask spreads widening rapidly

---

## Common Trading Mistakes

### Mistake 1: Too Much Leverage

**Problem:** 50x leverage feels like "more profit"
**Reality:** 2% move wipes you out

**Fix:** Start with 2-3x maximum until you understand the risks.

### Mistake 2: No Stop Loss

**Problem:** "It will come back"
**Reality:** Some positions never recover

**Fix:** Always set a stop loss before entering.

### Mistake 3: Ignoring Funding Costs

**Problem:** Holding leveraged position for weeks
**Reality:** Funding eats all your profits

**Fix:** Calculate funding costs before entering.

### Mistake 4: Trading Everything

**Problem:** Trying to catch every move
**Reality:** Fees and losses accumulate

**Fix:** Focus on high-conviction trades only.

---

## Summary

| Concept | Key Point |
|---------|-----------|
| **Spot Trading** | Buy/sell actual tokens |
| **Position** | Your exposure to price changes |
| **Long** | Profit when price goes up |
| **Short** | Profit when price goes down |
| **Perps** | Bet on price without owning asset |
| **Leverage** | Amplify gains AND losses |
| **Liquidation** | Position force-closed when margin insufficient |
| **Hedging** | Reduce risk with offsetting position |
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
