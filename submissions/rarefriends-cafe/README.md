# RareFriends Cafe

| | |
| --- | --- |
| **Project** | RareFriends Cafe |
| **Builder** | M4S4T0 · GitHub [@M4S4T0-V01D](https://github.com/M4S4T0-V01D) · X [@M4S4T0_V01D](https://x.com/M4S4T0_V01D) |
| **Category** | Character Spotlight (also entering Economy Potential and Token Activity) |
| **Source** | https://github.com/M4S4T0-V01D/rarefriends-cafe |
| **Playable preview** | https://m4s4t0-v01d.github.io/rarefriends-cafe/ *(TODO: confirm once Pages is live)* |
| **Stack** | FriendSDK **v0.1.2** CLI game (React 19, Canvas 2D, TypeScript) |

**One sentence:** A greyscale, faded-colour 2.5D isometric café sim, a Rare Friends take on *Moe Girl
Cafe 2*: your owned Rare Friend runs the café with a perk from its Generations family, guest Rare
Friends are the customers, and Rare Blend Capsules bought with (simulated) $RAREFRIENDS give café boosts.

## Wallet and network requirements

A browser wallet on **Robinhood mainnet (chain 4663)** holding a hardwired Rare Friends Generations NFT
(generation ≥ 1). FriendSDK handles wallet connection, Friend selection and the fresh ownership check.
Phones need a wallet with an in-app browser. **All RF balances, purchases and rewards are simulated**:
no contracts, signatures or transactions.

## Setup and run

```sh
git clone https://github.com/M4S4T0-V01D/rarefriends-cafe.git
cd rarefriends-cafe
npm ci
npm run dev        # http://localhost:4173  (npm run dev:lan to play from a phone on the same network)
npm run build      # static preview → games/rarefriends-cafe/.friendsdk/
```

Node.js 22+. FriendSDK v0.1.2 is vendored as a tarball packed from the official `v0.1.2` tag.

## How to play

- **Tap a guest** (or press their table number, 1–8) to take the order. The kitchen cooks it.
- When the counter bell rings, **tap the counter** (or press C). Your Friend picks up the ready dishes and delivers them.
- Tap the floor or use **WASD / arrows** to walk. **E / Space** acts on whatever is next to you. Tasks queue with numbered markers. X clears the queue.
- Fast service earns bigger tips in **Beans**, an in-café soft currency that is not RF. Spend Beans on new dishes, tables (3→8), espresso machine levels, five ambience levels, helper Friends who serve on their own, and chef Friends who add kitchen slots.
- A day lasts 150 s and ends with a summary. Guests leave unhappy when their patience runs out, which lowers your rating.
- **Manager perk by family:** Skeleton cooks faster · Mask +10% tips · Family faster helpers · Cellular carries 3 · Asymmetry 12% double pay · Hoverer moves 30% faster · Colossus +25% patience · Sparkling +0.5★ · Hollow +15% arrivals.
- Sound is off by default (♪ button or Settings). Reduce motion is in Settings and also follows the system setting. Loading and error states have a retry.

### Rare Blend Capsules: RF costs, odds and rules (simulated)

| Rule | Value |
| --- | --- |
| Capsule price | **1 RF** (`1000000000000000000` base units) |
| House Blend | 60% (6,000 bps) · 0.5 RF · kept: +3% tips per bag (max 5) |
| Silver Roast | 28% (2,800 bps) · 1 RF · kept: unlocks the Silver Latte special |
| Moonlight Roast | 10% (1,000 bps) · 2 RF · kept: unlocks the Moonlight Parfait, +10% patience |
| Golden Bean | 2% (200 bps) · 5 RF · kept: Genesis VIP guests (18% of arrivals) pay 3× |
| Expected value | **0.88 RF** per capsule |
| Consumable | One capsule opens into exactly one blend; single settlement, no reroll |
| Backing | Each purchased or pending capsule reserves 5 RF; kept blends keep their fixed RF backing |
| Redemption | Fixed value, no expiry. Redeeming removes that blend's café bonus (keep-or-redeem choice). |

Capsules use the SDK chance-game client (`buy` / `play` / `settle` / `redeem`) with runtime confirmations.
Proposed future RF integrations, which need APIs beyond SDK v0.1.2: persistent saves, RF-priced décor with burn,
live Dice-RNG capsules, café visits with RF tips, and staff revenue share.

### Credits

Café scenery, dish icons and procedural guest Friends are original canvas code. The manager uses the selected
Friend's canonical Generations sprite. Regulars #7730 and #3412 use canonical sample frames from FriendSDK v0.1.2.
The sound is the FriendSDK procedural kit. Rare Friends artwork is used under the FriendSDK NOTICE. Inspired by
*Moe Girl Cafe 2*; no assets from it are used.

## Checks and known issues

| Check | Result |
| --- | --- |
| `npm run typecheck` (tsc strict) | Pass |
| `npm test`: 10 engine tests (serve loop, patience, day cycle, purchases, helpers, blends, perks, economy table) | Pass |
| `npx friendsdk check` | Pass: expected reward 0.88 RF, max 5 RF |
| `npx friendsdk test` smoke check (SDK mock wallet) | Pass |
| Browser gameplay check at 960 px (keyboard serve loop, capsule buy → open → keep, upgrades, mute) and 360 px (touch) | Pass |
| Real-wallet playtest on Robinhood mainnet | **TODO** by the builder before final submission |

Known limitations: progress resets on reload (the SDK sandbox has no save API). Guest Friends are procedural
art in the Rare Friends style rather than specific tokens, because the game never scans the collection. Wallet
support is the SDK's (injected / EIP-6963; no WalletConnect). No wallet or fund risk: nothing is signed or sent.
