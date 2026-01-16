# NFTs Complete Guide: Digital Ownership on Blockchain

**Reading Time:** ~45 minutes
**Audience:** Users who understand crypto basics
**Level:** Intermediate
**Updated:** January 2026

---

## What You'll Learn

This document covers everything about NFTs:
- What NFTs actually are (beyond the hype)
- How ownership and trading works
- Technical standards and infrastructure
- Use cases: art, gaming, membership, RWA
- How to evaluate and stay safe
- The marketplace ecosystem

By the end, you'll understand what NFTs are, how they work, and how to participate safely.

---

## Quick Acronym Reference

| Acronym | What It Means |
|---------|---------------|
| **NFT** | Non-Fungible Token |
| **cNFT** | Compressed NFT |
| **pNFT** | Programmable NFT |
| **IPFS** | InterPlanetary File System |
| **IP** | Intellectual Property |
| **RWA** | Real-World Asset |

---

## Part 1: What Are NFTs?

### The Simple Explanation

**NFT = Non-Fungible Token = A unique digital item with verified ownership.**

"Fungible" means interchangeable. A dollar is fungible: any $1 bill equals any other $1 bill.

"Non-fungible" means unique. The Mona Lisa is non-fungible: there's only one original.

NFTs are digital items that work like the Mona Lisa: each one is unique, provably owned, and can be bought/sold.

### Fungible vs Non-Fungible

| Aspect | Fungible (SOL) | Non-Fungible (NFT) |
|--------|---------------|-------------------|
| **Identity** | Interchangeable | Each is unique |
| **Supply** | Many identical units | One of each |
| **Value** | Same per unit | Varies by item |
| **Example** | 1 SOL = 1 SOL | This specific artwork |

### What Makes NFTs Different

**Traditional digital files:**
- Anyone can copy perfectly
- No way to verify "original"
- Creator loses control after sharing

**NFTs:**
- Ownership recorded on blockchain
- History of every transfer
- Original can be verified
- Creator can earn royalties on resales

---

## Part 2: How NFT Ownership Works

### The Ownership Model

When you "own" an NFT:
- Blockchain records your address as the owner
- Only your private key can transfer it
- Anyone can verify your ownership
- No one can take it without your permission

### What You Actually Own

**You typically own:**
- The NFT token itself
- Right to display it
- Right to sell/transfer it

**You typically don't own:**
- The underlying intellectual property
- Commercial rights (unless specified)
- The "original" artwork (just a verified copy)

**License varies by project.** Some NFTs grant full commercial rights (you can make merchandise). Most don't.

### Proving Ownership

```
How verification works:

1. You claim to own NFT #1234
2. Someone queries the blockchain
3. Blockchain shows: "NFT #1234 is at address 0x123..."
4. You prove you control that address (sign a message)
5. Ownership verified
```

This works without revealing your private key.

---

## Part 3: Creator Royalties

### How Royalties Work

**The innovation:** NFT creators can earn on every resale, forever.

**Traditional art:**
- Artist sells painting for $1,000
- Collector sells for $100,000 later
- Artist gets: $0 from the appreciation

**NFT royalties:**
- Creator mints NFT, sets 5% royalty
- First sale: $1,000 (creator gets $1,000)
- Resale for $100,000: creator gets $5,000 automatically
- Every future sale: creator gets 5%

### Royalty Enforcement

**Problem:** Not all marketplaces honor royalties.

**pNFT Solution:** Programmable NFTs enforce royalties at the blockchain level.
- Built into the smart contract
- Marketplaces can't bypass
- Creator always gets paid

**Reality check:** Many older NFTs don't have enforced royalties. Check before buying if you care about supporting creators.

---

## Part 4: Technical Standards (Solana)

### NFT Standards on Solana

**SPL Token Standard**
The basic standard for all tokens on Solana. NFTs use this with:
- Supply = 1 (only one exists)
- Decimals = 0 (can't be split)

**Metaplex Standard**
Adds NFT-specific features:
- Metadata (name, image, attributes)
- Collections (grouping related NFTs)
- Creator verification
- Royalty support

### Types of Solana NFTs

**Traditional NFT (SPL)**
- Full data on-chain
- Higher cost (~$1.50 per NFT)
- Fast queries
- Best for: High-value items, items used in DeFi

**Compressed NFT (cNFT)**
- Uses merkle tree compression
- Much cheaper (~$0.05 per NFT)
- Requires index service for queries
- Best for: Large collections, profile pictures

**Programmable NFT (pNFT)**
- Enforced royalties at protocol level
- Transfer rules built-in
- Best for: Creators who want guaranteed royalties

### On-Chain vs Off-Chain Data

**What's on blockchain:**
- Token itself
- Owner address
- Metadata link (URI)
- Creator and royalty info

**What's off-chain:**
- Image/video files (too large for blockchain)
- Detailed metadata
- Stored on IPFS or Arweave

**Why this matters:**
If the off-chain storage fails, your NFT might show a broken image. Quality projects use permanent storage (Arweave).

---

## Part 5: NFT Metadata

### What Metadata Contains

```json
{
  "name": "Cool NFT #1234",
  "description": "Part of the Cool Collection",
  "image": "https://arweave.net/abc123.png",
  "attributes": [
    {"trait_type": "Background", "value": "Blue"},
    {"trait_type": "Eyes", "value": "Laser"},
    {"trait_type": "Rarity", "value": "Legendary"}
  ]
}
```

### Attributes and Rarity

**Attributes** define unique traits:
- Background, clothes, accessories
- Special features
- Each combination is unique

**Rarity** comes from attribute frequency:
- If only 1% have "Diamond Eyes," that's rare
- Rare traits typically = higher value
- Rarity tools rank NFTs by trait scarcity

### Metadata Reliability

**Watch out for:**
- Centralized hosting (can disappear)
- Unverified metadata (could be fake)
- Broken image links

**Good signs:**
- IPFS or Arweave storage (decentralized)
- Verified creator
- Established collection

---

## Part 6: NFT Use Cases

### Digital Art & Collectibles

The original NFT use case:
- Artists mint limited editions
- Collectors own verified originals
- Royalties support ongoing creation

**Success factors:**
- Creator reputation
- Community engagement
- Actual artistic quality

### Gaming Assets

Players own in-game items as NFTs:
- Weapons, armor, skins, characters
- Tradeable on marketplaces
- Potentially usable across games
- Persist even if game shuts down

**Current state:** Growing, but limited cross-game compatibility.

### Membership & Access

NFT = membership card:
- Discord access
- Exclusive content
- Early access to drops
- VIP benefits

**Examples:**
- Trading fee discounts for NFT holders
- Behind-the-scenes content for fans
- Governance votes in communities

### Brand Loyalty Programs

Companies issuing NFTs:
- Starbucks Odyssey (earn NFTs visiting stores)
- Nike (digital sneaker collectibles)
- Sports teams (fan tokens)

**Value proposition:**
- Gamification of loyalty
- Secondary market for rewards
- Data on customer behavior

### Real-World Assets (RWA)

Traditional assets as NFTs:
- Tokenized real estate (fractional ownership)
- Treasury bonds on-chain
- Commodities (gold-backed tokens)

**Benefits:**
- 24/7 trading
- Fractional ownership
- Instant settlement
- Global access

### Credentials & Certificates

Verifiable credentials as NFTs:
- University degrees
- Professional certifications
- Event attendance (POAPs)

**Benefits:**
- Impossible to forge
- Instant verification
- Portable (you own it forever)

---

## Part 7: Evaluating NFTs

### What to Check Before Buying

**Creator verification:**
- Is the creator verified on marketplace?
- Do they have a track record?
- Can you verify their identity?

**Collection health:**
- Active trading volume?
- Floor price stable or declining?
- Community still engaged?

**Technical quality:**
- Metadata stored permanently?
- Royalties enforced (pNFT)?
- Smart contract audited?

### Red Flags

**Rug pull warning signs:**
- Anonymous team
- Unrealistic promises
- Pressure to buy immediately
- No clear roadmap or utility

**Wash trading indicators:**
- Same wallet buying/selling repeatedly
- Volume spikes without price movement
- Suspiciously consistent sales

**Metadata risks:**
- Image hosted on personal server
- Unverified collection
- Missing or incomplete metadata

### Rarity Analysis

**How rarity works:**
1. Collection has 10,000 NFTs
2. Each has traits (background, eyes, clothes)
3. Some traits are common (50% have blue background)
4. Some are rare (1% have diamond eyes)
5. Rarity score combines all trait frequencies

**Rarity ≠ value, but often correlates.**

---

## Part 8: NFT Marketplaces

### Major Solana Marketplaces

**Magic Eden**
- Largest Solana marketplace (~50% share)
- Enforces creator royalties
- Comprehensive collection coverage

**Tensor**
- Real-time trading features
- Live streaming auctions
- Smaller but growing

**Others:**
- Solanart (community focused)
- Various specialized marketplaces

### How Marketplace Fees Work

```
Selling an NFT for $1,000:

Buyer pays: $1,000

Distribution:
- Creator royalty (5%): $50
- Marketplace fee (2%): $20
- Seller receives: $930
```

Fees vary by marketplace and collection.

### Listing and Buying

**To list (sell):**
1. Connect wallet to marketplace
2. Select NFT to sell
3. Set price (fixed or auction)
4. Sign listing transaction
5. NFT stays in your wallet until sold

**To buy:**
1. Browse marketplace
2. Find NFT you want
3. Click "Buy Now" or place bid
4. Sign purchase transaction
5. NFT transferred to your wallet

---

## Part 9: NFT Security

### Common Scams

**Fake marketplaces:**
- Clone site looks identical to real one
- You "list" NFT, scammer takes it
- Prevention: Bookmark official URLs only

**Phishing:**
- "Verify your collection" messages
- Links to fake wallet connect
- Scammer gains access
- Prevention: Never click links in DMs

**Rug pulls:**
- Team hypes collection
- Takes money, abandons project
- NFTs become worthless
- Prevention: Research team thoroughly

**Malicious contracts:**
- Approve "unlimited" access
- Scammer drains your wallet
- Prevention: Read transaction details carefully

### Security Best Practices

**Before connecting:**
- Verify you're on the official site
- Check URL carefully (phantom.io vs phantomm.io)
- Use bookmarks, not links

**Before signing:**
- Read what the transaction does
- Understand what you're approving
- Be suspicious of "unlimited" approvals

**After buying:**
- Verify NFT appears in your wallet
- Check metadata loads correctly
- Consider hardware wallet for valuable NFTs

### Protecting Valuable NFTs

For high-value NFT holdings:
- Use hardware wallet
- Separate wallet for marketplace interactions
- Revoke unused marketplace approvals
- Enable all available security features

---

## Part 10: NFT Trading Strategy

### Floor Price

**What it is:** The lowest listed price in a collection.

```
Collection "CoolCats" has 10,000 NFTs
- 500 listed for sale
- Cheapest listing: 5 SOL
- Floor price = 5 SOL
```

Floor gives you a baseline value. Any NFT in the collection is worth at least the floor (if you can sell at floor).

### Rarity Premium

NFTs with rare traits often sell above floor:
- Floor: 5 SOL
- Rare traits: 10-50 SOL
- 1 of 1: 100+ SOL

### Liquidity Considerations

**Liquid collections:**
- High volume, daily trades
- Can sell quickly at floor
- Smaller spread between bid/ask

**Illiquid collections:**
- Low volume, few buyers
- May wait days/weeks to sell
- May need to discount significantly

### When to Buy/Sell

**Buy signals:**
- New utility announced
- Team delivering on roadmap
- Floor stabilizing after decline
- Strong community engagement

**Sell signals:**
- Team going quiet
- Declining daily volume
- Community losing interest
- Floor breaking down repeatedly

---

## Part 11: NFTs in Wallets

### Basic Display

Every NFT wallet should show:
- Image (from metadata)
- Name and collection
- Current floor price (if available)
- Your cost basis (if tracked)

### Trading Integration

Good wallets integrate marketplaces:
- List for sale without leaving wallet
- See offers on your NFTs
- Quick buy from search

### Portfolio Features

Advanced features:
- Total NFT portfolio value
- Unrealized P&L
- Rarity rankings
- Price alerts

---

## Part 12: Future of NFTs

### Growing Areas

**Gaming:** In-game item ownership becoming standard.

**RWA:** Traditional assets moving on-chain.

**Credentials:** Verifiable achievements and certifications.

**Membership:** NFTs as access passes to communities and services.

### Declining Narratives

**Pure speculation:** "Buy because number go up" is unsustainable.

**Jpeg-only value:** NFTs without utility struggling.

**Copy-paste collections:** Derivative projects with no innovation.

### Long-Term Value

NFTs that will likely retain value:
- Established creator reputation
- Clear utility beyond speculation
- Strong community
- Technical innovation
- Real-world integration

---

## Summary

| Concept | Key Point |
|---------|-----------|
| **NFT** | Unique digital item with verified ownership |
| **Ownership** | Recorded on blockchain, controlled by private key |
| **Royalties** | Creators can earn on every resale |
| **Metadata** | Defines traits, stored on/off chain |
| **Rarity** | Trait scarcity often correlates with value |
| **Floor** | Lowest listed price in collection |
| **Security** | Verify sites, read transactions, use hardware wallets |

---

## What's Next?

Now that you understand NFTs, the next document covers:
- **Advanced topics:** Prediction markets, complex strategies
- **Liquidation mechanics in depth**
- **MEV and advanced DeFi concepts**

Continue to: [06_ADVANCED_TOPICS.md](./06_ADVANCED_TOPICS.md)

---

## Quick Reference: NFT Evaluation Checklist

Before buying an NFT, check:

- [ ] Creator verified on marketplace?
- [ ] Team identity known (not anonymous)?
- [ ] Collection has trading volume?
- [ ] Floor price stable (not collapsing)?
- [ ] Metadata stored permanently (IPFS/Arweave)?
- [ ] Royalties enforced (if you care about supporting creator)?
- [ ] Utility beyond speculation?
- [ ] Community still active?
- [ ] You can afford to lose this money?

---

**Last Updated:** January 16, 2026
**Version:** 2.0
