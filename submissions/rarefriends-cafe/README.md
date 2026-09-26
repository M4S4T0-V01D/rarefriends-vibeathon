# RareFriends Cafe

**▶ Play:** https://m4s4t0-v01d.github.io/rarefriends-cafe/ · **Source:** https://github.com/M4S4T0-V01D/rarefriends-cafe

![RareFriends Cafe: an isometric greyscale shop run by Rare Friends](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-cafe/main/docs/cafe.png)

| | |
| --- | --- |
| **Project** | RareFriends Cafe |
| **Builder** | M4S4T0 · GitHub [@M4S4T0-V01D](https://github.com/M4S4T0-V01D) |
| **Category** | Character Spotlight (also entering Economy Potential and Token Activity) |
| **Source repository** | https://github.com/M4S4T0-V01D/rarefriends-cafe |
| **Playable preview** | https://m4s4t0-v01d.github.io/rarefriends-cafe/ (GitHub Pages, deployed by CI from `main`) |
| **Stack** | FriendSDK **v0.1.2** (SDK `GameHost` + CLI game build), React 19, Canvas 2D, TypeScript |

**One sentence:** A greyscale, faded-colour 2.5D isometric shop sim, a Rare Friends take on *Moe Girl Cafe 2*.
Your owned Rare Friend manages the shop with a perk from its Generations family. Your other owned Friends work
as staff and guest Rare Friends are the customers. You choose the shop type, arrange it on a tile grid, and
progress saves per wallet. Rare Recipe Capsules spend (simulated) $RAREFRIENDS for shop bonuses.

| Choose your shop | Build mode on the tile grid | Your owned Friend as chef |
| --- | --- | --- |
| ![Shop picker](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-cafe/main/docs/shop-picker.png) | ![Build mode](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-cafe/main/docs/build.png) | ![Owned chef](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-cafe/main/docs/owned-chef.png) |
| **Staff slots** | **Rare Recipe Capsule** | **Saved per wallet** |
| ![Staff](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-cafe/main/docs/staff.png) | ![Capsule](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-cafe/main/docs/capsule.png) | ![Welcome back](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-cafe/main/docs/welcome-back.png) |

## Wallet and network requirements

A browser wallet on **Robinhood mainnet (chain 4663)** holding a hardwired Rare Friends Generations NFT
(generation ≥ 1). FriendSDK's `GameHost` handles wallet connection, Friend selection and the fresh ownership
check. Phones need a wallet with an in-app browser (for example MetaMask Mobile). **All RF balances, purchases
and rewards are simulated**: no contracts, signatures or transactions.

## Setup and run

```sh
git clone https://github.com/M4S4T0-V01D/rarefriends-cafe.git
cd rarefriends-cafe
npm ci
npm run dev        # http://localhost:4173   (npm run dev:lan to play from a phone on the same network)
npm run build      # static site → games/rarefriends-cafe/.friendsdk/
```

Node.js 22+. FriendSDK v0.1.2 is vendored as a tarball packed from the official `v0.1.2` tag.

## How to play

- **Choose your shop:** coffee & sweets café, seafood restaurant, pastry shop, burger diner or Asian noodle house. Each has its own 9-dish menu, dish art and kitchen station.
- **Serve:** tap a guest (or press their table number, 1–9/0) to take the order. When the bell rings, tap the counter (C); your Friend picks up and delivers. WASD/arrows walk, E acts nearby, X clears the task queue.
- **Earn Beans** (an in-shop soft currency, not RF) through tips for fast service. Spend them on dishes, kitchen station levels, staff slots, furniture and designs. A day lasts 150 s; guests leave unhappy when patience runs out.
- **Staff:** 1 slot to start, up to 5 (120/280/520/900 Beans at levels 2/3/5/7). Fill a slot with **another Friend you own** (canonical sprite; 25% faster and 2-dish trays as a waiter, 10% faster as a chef) or a guest applicant. Waiters serve on their own; each chef adds a kitchen slot.
- **Build (B):** an 11 × 11 tile grid. Place, rotate (R), move and sell tables (60; max 3 + level), plants, rugs, lamps, bookshelves, a record player and a piano. Choose 6 wallpapers and 6 floors. Placements that would block guests or staff are refused. Décor raises ambience for better tips, patience and more guests.
- **Manager perk by family:** Skeleton cooks faster · Mask +10% tips · Family faster staff · Cellular carries 3 · Asymmetry 12% double pay · Hoverer moves 30% faster · Colossus +25% patience · Sparkling +0.5★ · Hollow +15% arrivals.
- **Progress saves per wallet address** (on this device) and restores when you reconnect.
- Sound is off by default (♪ or Settings). Reduce motion is in Settings and follows the system setting. Loading and error states have a retry.

### Rare Recipe Capsules: RF costs, odds and rules (simulated)

| Rule | Value |
| --- | --- |
| Capsule price | **1 RF** (`1000000000000000000` base units) |
| House Secret | 60% (6,000 bps) · 0.5 RF · kept: +3% tips per recipe (max 5) |
| Silver Recipe | 28% (2,800 bps) · 1 RF · kept: unlocks your shop's silver special |
| Moonlight Recipe | 10% (1,000 bps) · 2 RF · kept: unlocks your shop's moonlight special, +10% patience |
| Golden Recipe | 2% (200 bps) · 5 RF · kept: Genesis VIP guests (18% of arrivals) pay 3× |
| Expected value | **0.88 RF** per capsule |
| Consumable | One capsule opens into exactly one recipe; single settlement, no reroll |
| Backing | Each purchased or pending capsule reserves 5 RF; kept recipes keep their fixed RF backing |
| Redemption | Fixed value, no expiry. Redeeming removes that recipe's bonus (keep-or-redeem choice). |

Capsules use the SDK chance-game client (`buy` / `play` / `settle` / `redeem`) with runtime confirmations.
**Economy design:** Beans are earn-only, RF is a boost rather than a paywall, and owned staff reward holding more
Generations NFTs. Proposed future RF integrations, which need APIs beyond SDK v0.1.2: cloud saves, RF-priced
premium furniture and seasonal themes with burn, live Dice-RNG capsules, shop visits with RF tips, and staff
revenue share.

### SDK integration notes

The runtime page is the SDK's `GameHost`, unchanged in behaviour. `host/runtime.tsx` adds a read-only
`readOwnedFriends` roster (account-filtered, `eth_accounts` only) and per-wallet `localStorage` saves, because the
sandbox has neither. The sandboxed game receives both over `postMessage` from its parent window. It uses them
only when the roster contains the manager the runtime just verified. There are no signatures or extra prompts.

### Credits

Scenery, furniture, 23 dish icon shapes, wallpapers, floors and procedural guest Friends are original canvas code.
The manager and owned staff use their canonical Generations sprites. Regulars #7730 and #3412 use canonical sample
frames from FriendSDK v0.1.2. The sound is the FriendSDK procedural kit. Rare Friends artwork is used under the
FriendSDK NOTICE. Inspired by *Moe Girl Cafe 2*; no assets from it are used.

## Checks and known issues

| Check | Result |
| --- | --- |
| `npm run typecheck` (tsc strict, game + host) | Pass |
| `npm test`: 19 engine tests (shops, service loop, patience, day cycle, placement rules, ambience, staff, save/restore + tamper rejection, perks, economy) | Pass |
| `npm run check` (`friendsdk check`) | Pass: expected reward 0.88 RF, max 5 RF |
| Browser, SDK CLI host, 960 px: shop pick, keyboard service, build (pointer + keyboard), floor designs, staff hire, capsule buy → open → keep, mute | Pass |
| Browser, 360 px touch: service and build bar | Pass |
| Browser, custom host, two-Friend mock wallet: owned #3412 hired as chef with canonical art, save written for the wallet address, reload → restored | Pass |
| All of the above in GitHub Actions before each Pages deploy | Pass |
| Real-wallet playtest on Robinhood mainnet | By the builder (the build environment can't reach mainnet) |

Known limitations: saves are per device and browser, keyed by wallet address, and are client-side. Capsule
balances reset on reload (SDK session ledger). Guest Friends are procedural art in the Rare Friends style rather
than specific tokens. The owned-staff roster depends on the RPC returning the wallet's transfer history; guest
applicants work regardless. Wallet support is the SDK's (injected / EIP-6963; no WalletConnect). There is no wallet
or fund risk: nothing is signed or sent.
