# NFT User Experience Strategy for Solflare

**Reading Time:** ~25 minutes
**Audience:** Product Managers & Designers (Solana-focused)
**Updated:** January 2026

---

## What's in This Document

Complete UX framework for building NFT features in Solflare:

- **Information Architecture**: How to organize NFT features in wallet
- **Display & Discovery**: Showing NFTs, finding collections, rarity
- **Trading UX**: In-wallet buying/selling, offer system, price visibility
- **Creator Features**: Minting, royalty management, analytics
- **Security & Trust**: Scam prevention, metadata validation, risk scoring
- **Mobile vs Desktop**: Platform-specific considerations
- **Accessibility**: Ensuring non-technical users can use NFT features

**Core principle:** NFTs must feel native to wallet, not bolted-on. User shouldn't feel like they're leaving Solflare to trade.

---

## Part 1: Information Architecture

### Main Navigation Structure

**Current Solflare structure:**
- Home (balance, recent transactions)
- Send/Receive
- Settings
- (NFTs feature TBD)

**Proposed NFT integration:**

**Option A: Tab-based (Simplest)**
```
[Home] [Send] [NFTs] [Settings]
```
Pros: Simple, discoverable
Cons: Clutters top nav

**Option B: Sidebar (Recommended)**
```
Home
  ├─ Portfolio (balance overview)
  └─ Recent Activity
Send & Receive
NFTs
  ├─ My Collections
  ├─ Marketplace
  ├─ Creator Tools
  └─ Gaming Assets
Staking (existing)
Settings
```
Pros: Organized, expandable, clean UI
Cons: Takes more space

**Option C: Hub-style (Best for scale)**
```
Home (default landing page)
  ├─ Quick actions (Send, Receive, Sell NFT)
  ├─ Portfolio (crypto + NFT holdings)
  └─ Recent activity
Hub (toggleable from home)
  ├─ NFTs (your collection)
  ├─ Marketplace (trading)
  ├─ Creator Studio (if creator)
  ├─ Yield (staking + LP)
  └─ DAO (governance - future)
```
Pros: Scalable, doesn't clutter main nav
Cons: Requires user education

**Recommendation:** Option B (Sidebar) for initial launch, plan for Option C as features grow.

---

### NFT Hub Structure

```
NFTs
├─ My Collections
│  ├─ [Collection 1]
│  │  ├─ [NFT #1]
│  │  │  ├─ View Details
│  │  │  ├─ Sell
│  │  │  ├─ Transfer
│  │  │  └─ Stake
│  │  ├─ [NFT #2]
│  │  └─ (pagination)
│  └─ [Collection 2]
├─ Analytics (rarity, floor price, portfolio value)
├─ Marketplace
│  ├─ Browse Collections
│  ├─ Search / Filter
│  ├─ Create Offer
│  └─ Offers Received
└─ Creator Tools (if user is creator)
   ├─ Launch Collection
   ├─ Manage Existing
   └─ Royalty Dashboard
```

---

## Part 2: NFT Display & Discovery

### NFT Gallery View

**Thumbnail Grid:**
```
┌─────────────────────────────────────┐
│ My Collections  Filter: All ▼        │
├─────────────────────────────────────┤
│ ┌────────┐ ┌────────┐ ┌────────┐   │
│ │ [IMG]  │ │ [IMG]  │ │ [IMG]  │   │
│ │DeGod#1 │ │BAYC#42 │ │  Blur  │   │
│ │Floor   │ │Floor   │ │Floor   │   │
│ │50 SOL  │ │200 SOL │ │2 SOL   │   │
│ │▼ 25%   │ │▲ 10%   │ │ —  0%  │   │
│ └────────┘ └────────┘ └────────┘   │
│ ┌────────┐ ┌────────┐                │
│ │ [IMG]  │ │ [IMG]  │                │
│ └────────┘ └────────┘                │
└─────────────────────────────────────┘
```

**Metadata displayed per NFT:**
- Collection name (linked to collection page)
- NFT ID/name
- Floor price (if collection has marketplace floor)
- Price change indicator (24h change, color-coded: red = down, green = up)
- Quick action: Tap to see full details

**Filtering/Sorting:**
- Filter by collection
- Filter by rarity (upcoming, rare, common)
- Sort by: acquired date, floor price, value
- Search by name/ID

---

### NFT Detail View

**When user taps NFT thumbnail:**

```
┌─────────────────────────────────────┐
│ ← Back                              │
├─────────────────────────────────────┤
│                                     │
│          [Large Image]              │
│      (Zoomable, high res)           │
│                                     │
├─────────────────────────────────────┤
│ DeGods #4521                        │
│ Collection: DeGods                  │
│                                     │
│ Value Metrics                       │
│ ├─ You paid: 50 SOL ($4,000)        │
│ ├─ Floor price: 50 SOL              │
│ ├─ Current value*: 50 SOL ($4,000)  │
│ ├─ P&L: +$0 (0%)                    │
│ └─ *Based on last floor update      │
│                                     │
│ Traits & Rarity                     │
│ ├─ Background: Purple (15% rarity)  │
│ ├─ Eyes: Diamond (2% rarity)        │
│ ├─ Mouth: Smile (30% rarity)        │
│ └─ Rarity Score: #124 / 10,000      │
│                                     │
│ Creator & Royalties                 │
│ ├─ Creator: @SomethingStudio        │
│ ├─ Royalty: 5% (✓ enforced)         │
│ └─ Earnings: You'll get 95% of sale │
│                                     │
│ Trading History                     │
│ ├─ Acquired: Dec 15, 2025 @ 50 SOL  │
│ ├─ Previous: Oct 10, 2025 @ 45 SOL  │
│ └─ [View full history]              │
│                                     │
│ [Sell] [Offer] [Transfer] [More...]│
└─────────────────────────────────────┘
```

**Information priorities:**
1. Image (primary)
2. Name, collection (identity)
3. Your cost basis + current value (financial)
4. Traits (collector interest)
5. Creator + royalty (transparency)
6. Trading history (education)

---

### Collection Page

**When user taps collection name:**

```
┌─────────────────────────────────────┐
│ ← Back          [Heart: Save]       │
├─────────────────────────────────────┤
│ DeGods (Banner image)               │
├─────────────────────────────────────┤
│ DeGods                              │
│ A Legendary Collection              │
│                                     │
│ Stats                               │
│ ├─ Floor: 50 SOL (+5% 24h)          │
│ ├─ Volume: 15M SOL/month            │
│ ├─ Owners: 8K                       │
│ ├─ Supply: 10K                      │
│ └─ Royalty: 5% (✓ enforced)         │
│                                     │
│ You own: 5 / 10,000                 │
│ ├─ Portfolio value: 250 SOL         │
│ └─ [View your items]                │
│                                     │
│ [Browse Market] [Create Offer]      │
│                                     │
│ Activity                            │
│ Last 24h: 150 sales @ avg 50 SOL    │
│ Last 7d: 950 sales @ avg 48 SOL     │
│                                     │
│ [View charts & analytics]           │
└─────────────────────────────────────┘
```

---

### Rarity Scoring & Analytics

**Rarity rank logic:**
- System analyzes all NFT traits in collection
- Calculates trait frequency (how rare is this trait?)
- Combines traits into rarity score
- Ranks NFT (e.g., #124 / 10,000 = top 1.24%)

**UX for rarity:**

**Option A: Simple (Current approach)**
- Show rarity number (#124 / 10,000)
- Color-code: Green (rare) → Red (common)

**Option B: Detailed (Better education)**
```
Rarity Score: 95/100 (Top 5%)
┌──────────────────────────┐
│ Rarity Components        │
├──────────────────────────┤
│ ◆ Eyes: Diamond          │
│   Rarity: 2%             │
│   Count: 200 / 10,000    │
│   Score: +25             │
│                          │
│ ◆ Background: Purple     │
│   Rarity: 15%            │
│   Count: 1,500 / 10,000  │
│   Score: +15             │
│                          │
│ ◆ Mouth: Smile           │
│   Rarity: 30%            │
│   Count: 3,000 / 10,000  │
│   Score: +8              │
│                          │
│ Your score: 95/100       │
│ Average: 50/100          │
│ Rank: #124 / 10,000      │
└──────────────────────────┘
```

**Recommendation:** Option B (more transparent, educates users on value)

---

## Part 3: Trading UX

### Selling an NFT

**Flow:**

```
User taps [Sell] button on NFT
    ↓
"Choose sell method"
├─ Fixed Price (list at price)
├─ Auction (highest bid wins)
└─ Offer (accept/reject specific offers)
    ↓
User selects "Fixed Price"
    ↓
Enter selling price
├─ Current floor: 50 SOL (suggested baseline)
├─ Your last purchase: 50 SOL
├─ Price field: [______] SOL
└─ Royalty disclosure: Creator gets 5% = (5% of price)
    ↓
Marketplace selection
├─ Magic Eden (✓ recommended, enforces royalties)
├─ Tensor (fast execution, enforces royalties)
└─ Other... (warning: some don't enforce royalties)
    ↓
Review & confirm
├─ NFT: DeGods #4521
├─ Price: 50 SOL ($4,000)
├─ Creator royalty: 2.5 SOL ($200)
├─ You receive: 47.5 SOL ($3,800)
├─ Marketplace fee: 1 SOL ($80)
├─ Listing on: Magic Eden
└─ [List] [Cancel]
    ↓
Listing created
├─ Success message
├─ Link to view on marketplace
└─ Option to unlist anytime
```

**Key UX principles:**
1. **Price anchoring**: Show floor, your cost, collection avg
2. **Royalty transparency**: Clear calculation (creator gets X%)
3. **Marketplace choice**: Let user pick (but warn about non-enforcing)
4. **Final summary**: Confirm amount they receive

---

### Buying an NFT

**Flow in Solflare:**

Option A: Browse in wallet
```
[Browse Marketplace]
    ↓
User browses collections
    ↓
Finds NFT, taps to view
    ↓
Shows price + details
    ↓
[Make Offer] button (primary action)
[View on Magic Eden] link (fallback)
```

Option B: Direct marketplace link
```
User taps NFT collection
    ↓
[Browse Magic Eden] button
    ↓
Opens Magic Eden in browser
    ↓
User buys there
    ↓
Returns to Solflare
    ↓
Wallet auto-updates (new NFT appears in gallery)
```

**Recommendation:** Option A (keep user in wallet longer). But allow Option B as fallback.

---

### Offers (Bidding System)

**Create Offer flow:**

```
User finds NFT they like but price is high
    ↓
[Make Offer] button
    ↓
"How much would you offer?"
├─ Floor price: 50 SOL
├─ Your offer: [______] SOL (e.g., 40 SOL)
└─ Duration: [7 days] ▼
    ↓
Confirm offer
├─ NFT: DeGods #4521
├─ Your offer: 40 SOL
├─ Expires: Jan 20, 2026
├─ Approval: (biometric auth to confirm spending)
└─ [Send Offer] [Cancel]
    ↓
Success
├─ Seller notified
├─ Will expire in 7 days
└─ You can cancel anytime
```

**Receive Offer flow:**

```
Notification: "Someone offered 40 SOL for your DeGods #4521"
    ↓
View offer details
├─ Offered by: @Collector123
├─ Offer: 40 SOL
├─ Expires: Jan 20, 2026
├─ Your asking: 50 SOL
└─ Difference: -10 SOL
    ↓
[Accept] [Reject] [Counter Offer] options
```

---

## Part 4: Creator Features

### Minting Flow

**For non-technical creators:**

```
[Creator Tools] → [Launch Collection]
    ↓
"Create your NFT collection"
    ├─ Collection name: [DeGods 2] [✓ available]
    ├─ Description: [Artists' notes...]
    ├─ Total supply: [5000]
    ├─ Royalty %: [5] (blockchain enforced)
    ├─ Creator address: [@YourAddress]
    └─ Terms: "I confirm I own image rights"
    ↓
Upload NFT data
├─ [Upload Image] (drag & drop)
│  └─ Auto-convert to IPFS
├─ Metadata template:
│  ├─ NFT name: [Daydream #1]
│  ├─ Description: [description...]
│  └─ Attributes:
│     ├─ Background: Purple
│     ├─ Eyes: Diamond
│     └─ [Add more traits...]
└─ [Generate multiple] (if variations)
    ↓
Review & confirm
├─ Collection name: DeGods 2
├─ Supply: 5,000 NFTs
├─ Royalty: 5% (to @YourAddress)
├─ Metadata: 5,000 items ready
├─ Storage: IPFS (decentralized)
├─ Cost: ~0.5 SOL ($0.04)
└─ [Create Collection] [Cancel]
    ↓
Collection live
├─ Share link: solflare.com/nft/DeGods2
├─ Mint link: solflare.com/mint/DeGods2
├─ [Share to Twitter/Discord]
└─ Creator Dashboard available
```

**Key UX:**
1. **Simplify metadata**: Pre-fill common traits
2. **Bulk upload**: Support CSV for 1000s of NFTs
3. **IPFS auto**: Handle decentralized storage without user knowing
4. **Cost transparency**: Show exact SOL cost upfront

---

### Creator Dashboard

**Analytics for creators:**

```
Creator Dashboard: DeGods 2
├─ Collection Status
│  ├─ Live: 2,345 / 5,000 minted (46.9%)
│  ├─ Floor price: 2.5 SOL
│  ├─ Total volume: 15 SOL (6 sales)
│  ├─ Creator earnings: 0.75 SOL (from royalties)
│  └─ [View on marketplace]
│
├─ Royalty Tracking
│  ├─ Royalty rate: 5% (enforced)
│  ├─ Earnings this month: 2.5 SOL
│  ├─ Earnings all-time: 5.1 SOL
│  ├─ Top holder: @Collector (owns 3)
│  └─ [Export earnings report]
│
├─ Holder Insights
│  ├─ Total holders: 42
│  ├─ Floor holder: @Joe (owns 1)
│  ├─ Whale holders: (none > 10%)
│  ├─ Community strength: Medium
│  └─ [Send airdrop to holders]
│
├─ Recent Activity
│  ├─ Jan 12: @Alice bought #234 @ 2.5 SOL
│  ├─ Jan 11: @Bob bought #123 @ 2.3 SOL
│  ├─ Jan 10: 10 mints initiated
│  └─ [View full history]
│
└─ [Manage Collection] [Launch 2nd Collection]
```

---

## Part 5: Security & Trust

### Scam Prevention UX

**Warning system:**

```
NFT Detail View
┌──────────────────────────────────────┐
│ ⚠️ HIGH RISK: This collection is only│
│    2 weeks old. Rug pull risk is     │
│    higher in new projects.           │
│                                      │
│ Safety tips:                         │
│ • Check if team is doxxed            │
│ • Look for active development        │
│ • Read community reviews             │
│ • Start with small investment        │
│                                      │
│ [Learn more] [Ignore warning]        │
└──────────────────────────────────────┘
```

**Creator verification:**

```
Creator Info Section
├─ Creator: @SomethingStudio
├─ Verified: ✓ (verified via website + Twitter)
├─ Projects: 5 collections, $2M+ volume
├─ Community: 50K Discord members
├─ Social: @twitter linked, @discord linked
└─ Reputation score: 9.2/10
```

**Royalty enforcement indicator:**

```
Creator & Royalties
├─ Creator: @SomethingStudio
├─ Royalty: 5%
├─ Enforcement: ✓ On-chain (pNFT)
│  "Creator gets 5% on every resale,
│   enforced by Metaplex. Even if
│   you sell on non-cooperative
│   marketplace, royalty flows."
└─ Trust score: High
```

---

### Metadata Reliability

**Handle broken metadata:**

```
NFT Display
┌──────────────────────────────────┐
│ [Placeholder Image]              │
│ (Image metadata unavailable)     │
│                                  │
│ ⚠️ Metadata issue detected       │
│                                  │
│ This NFT's metadata link is      │
│ broken or unreachable. You still │
│ own this NFT on-chain, but we    │
│ can't display the image.         │
│                                  │
│ • Collection still valid         │
│ • You can still sell             │
│ • Image may return later         │
│ • [Try refreshing] [Report]      │
└──────────────────────────────────┘
```

**Why this matters:**
- IPFS links can become unavailable if pinning service dies
- Educates user that on-chain NFT persists even if image dies
- Reduces panic ("I lost my NFT!")

---

## Part 6: Mobile vs Desktop UX

### Mobile NFT Gallery

**Constraint: Small screen, vertical scrolling**

```
┌─────────────────────────────────────┐
│ NFTs                        [Filter] │
├─────────────────────────────────────┤
│ My Collections (3)                  │
│                                     │
│ ┌──────────────────────────────────┐│
│ │ DeGods (5 NFTs owned)             ││
│ │ Floor: 50 SOL ▲ 5%                ││
│ │ [View collection]                 ││
│ └──────────────────────────────────┘│
│                                     │
│ ┌──────────────────────────────────┐│
│ │ BAYC (1 NFT owned)                ││
│ │ Floor: 200 SOL ▼ 2%               ││
│ │ [View collection]                 ││
│ └──────────────────────────────────┘│
│                                     │
│ ┌──────────────────────────────────┐│
│ │ Blur (2 NFTs owned)               ││
│ │ Floor: 2 SOL → 0%                 ││
│ │ [View collection]                 ││
│ └──────────────────────────────────┘│
│                                     │
│ [Browse Marketplace] [Creator Tools]│
└─────────────────────────────────────┘
```

**NFT Detail on mobile:**

```
┌─────────────────────────────────────┐
│ ← Back                              │
├─────────────────────────────────────┤
│ DeGods #4521                        │
│ [Large image, swipeable]            │
├─────────────────────────────────────┤
│ Value                               │
│ You paid: 50 SOL                    │
│ Floor: 50 SOL                       │
│ P&L: +$0                            │
│                                     │
│ Traits                              │
│ Eyes: Diamond (2% rarity)           │
│ Background: Purple (15% rarity)     │
│                                     │
│ [Sell] [Offer] [Transfer]           │
│ [More options...]                   │
└─────────────────────────────────────┘
```

---

### Desktop NFT Gallery

**Advantage: More space**

```
┌─────────────────────────────────────────────────────────────┐
│ NFTs        Filter: All      Sort: Recent      [Search...]   │
├─────────────────────────────────────────────────────────────┤
│ ┌─────────┬─────────┬─────────┬─────────┬─────────┐         │
│ │ [IMG]   │ [IMG]   │ [IMG]   │ [IMG]   │ [IMG]   │         │
│ │DeGod#1  │BAYC#42  │ Blur#1  │DeGod#2  │ Blur#2  │         │
│ │50 SOL▼  │200 SOL▲ │2 SOL→   │50 SOL▲  │2 SOL→   │         │
│ │#124/10K │#234/10K │#542/10K │#125/10K │#543/10K │         │
│ └─────────┴─────────┴─────────┴─────────┴─────────┘         │
│ ┌─────────┬─────────┬─────────┐                             │
│ │ [IMG]   │ [IMG]   │ [IMG]   │                             │
│ └─────────┴─────────┴─────────┘                             │
└─────────────────────────────────────────────────────────────┘

Right sidebar (when NFT selected)
┌──────────────────────────┐
│ DeGods #4521             │
│                          │
│ [Full image + details]   │
│                          │
│ Price: 50 SOL            │
│ Floor: 50 SOL            │
│ P&L: +$0                 │
│                          │
│ Traits:                  │
│ • Eyes: Diamond (2%)     │
│ • Background: Purple     │
│                          │
│ Creator: SomethingStudio │
│ Royalty: 5% (enforced)   │
│                          │
│ [Sell] [Offer] [...]     │
└──────────────────────────┘
```

---

## Part 7: Information Hierarchy

### What Users Need at Each Step

**Discovery phase (first time):**
1. What is this NFT? (image, name)
2. How rare is it? (rarity score)
3. How much is it worth? (floor price, your cost)

**Trading phase (considering sale):**
1. What will I receive? (price - fees)
2. Can I sell it? (liquidity, time to sell)
3. Where do I sell? (marketplace choice)

**Creation phase (as creator):**
1. How do I mint? (simple steps)
2. What will it cost? (SOL cost)
3. How do I earn? (royalty tracking)

---

### Content Density by Page

**NFT Gallery: Low density**
- Large thumbnails (easy to scan visually)
- Minimal text (name, price, change indicator)
- Quick filters (collection, rarity, sort)

**NFT Detail: Medium density**
- Large image (primary focus)
- Organized sections (value, traits, creator, activity)
- Expandable details (trading history, holder info)

**Creator Dashboard: High density**
- Multiple metrics (mints, floor, volume, earnings)
- Charts (revenue over time)
- Tables (holder list, activity feed)

---

## Part 8: Accessibility Considerations

### For Non-Technical Users

**NFT concepts should be simplified:**

Don't say: "Mint pNFT to Metaplex standard with IPFS metadata URI"
Say: "Create your collection" (UI handles technical details)

Don't show: Merkle tree compression, state compression options
Say: "Small NFTs" (for cNFT) vs "Regular NFTs" (for SPL)

---

### For Non-Native English Speakers

- Short, clear labels
- Icons for key actions (⭐ for favorite, 💰 for price)
- Glossary for NFT terms
- Visual cues over text (color for rarity, charts for trends)

---

### For Accessibility (Screen readers, keyboard nav)

**NFT gallery:**
- Each NFT is focusable (keyboard nav)
- Alt text: "DeGods #4521, rarity rank 124 of 10,000, floor price 50 SOL"
- Tab order: Image → Name → Price → Rarity → Actions

**Forms (minting, selling):**
- Clear labels for each input field
- Helper text (floor price, suggested price)
- Confirmation before submitting (prevents accidental mints)

---

## Part 9: Engagement Features (Optional)

### Notifications

**Timeline-based:**
- "Floor price of your DeGods collection updated"
- "Offer received on your NFT"
- "Listing expired, view similar for sale"

**Configured by user:**
- Notify on floor change (5%+, 10%+, custom)
- Notify on offer received
- Notify on collection news (new listings, volume spikes)

---

### Social Features (Long-term)

**Showcase collections:**
```
Profile → Collections
├─ Public NFT profile
├─ "Favorite NFTs" showcase
├─ Trading activity visible
└─ Social metrics (followers, likes)
```

**Community:**
```
Collection page
├─ Holder discussion (comments)
├─ Tips from community
├─ Creator announcements
└─ Floor price predictions
```

---

## Part 10: Key UX Principles Summary

1. **Native to wallet**: NFT features feel like part of Solflare, not external
2. **Clarity over features**: Better to show 3 metrics clearly than 10 metrics confusingly
3. **Progressive disclosure**: Simple by default, detailed options on second tap
4. **Confidence building**: Risk warnings, creator verification, security indicators
5. **Speed**: Solana's advantage is speed—reflect that in responsive UI
6. **Transparency**: Show calculations (fees, royalties), not hidden surprises
7. **Reversible actions**: Can't undo mint, but can unlist anytime before sale
8. **Context preservation**: When user returns from marketplace, show where they were

---

## Recommended Design Sprint

**Week 1: NFT Gallery**
- Display, filtering, sorting
- Collection page, rarity rankings
- Basic metadata handling

**Week 2: Selling UX**
- Listing flow, price anchoring
- Marketplace selection, fee calculation
- Unlist, modify price

**Week 3: Security & Polish**
- Scam warnings, creator verification
- Metadata fallbacks
- Edge cases (broken images, slow loads)

**Week 4: Creator Tools (MVP)**
- Simple minting flow
- Creator dashboard (basic analytics)
- Royalty tracking

---

**Last Updated:** January 13, 2026
**Version:** 1.0
