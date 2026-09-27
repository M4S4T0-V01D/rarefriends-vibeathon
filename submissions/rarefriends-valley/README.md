# RareFriends Valley

**▶ Play:** https://m4s4t0-v01d.github.io/rarefriends-valley/ · **Preview page:** https://m4s4t0-v01d.github.io/rarefriends-valley/preview/ · **Source:** https://github.com/M4S4T0-V01D/rarefriends-valley

*Your Rare Friend inherits a little farm in a greyscale valley. Plant through four seasons, befriend a town where everyone is a Rare Friend, and film cute clips of it all.*

![RareFriends Valley: a greyscale isometric farm in summer with crops, a star windmill, a scarecrow and a golden statue of the player's Friend](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-valley/main/docs/farm-summer.png)

| | |
| --- | --- |
| **Project** | RareFriends Valley |
| **Builder** | M4S4T0 · GitHub [@M4S4T0-V01D](https://github.com/M4S4T0-V01D) |
| **Category** | Character Spotlight (also entering Economy Potential and Token Activity) |
| **Source repository** | https://github.com/M4S4T0-V01D/rarefriends-valley |
| **Playable preview** | https://m4s4t0-v01d.github.io/rarefriends-valley/ (GitHub Pages, deployed by CI from `main`) |
| **Preview page** | https://m4s4t0-v01d.github.io/rarefriends-valley/preview/ (seasons, features, a recorded clip, blessing odds, play button, and the game's music) |
| **Stack** | FriendSDK **v0.1.2** (SDK `GameHost` + CLI game build), React 19, Canvas 2D, WebAudio, MediaRecorder, TypeScript |

**One sentence:** A Harvest Moon–style farming life sim in 2.5D (with a rotating camera), starring your owned Rare
Friend as the farmer in a town where every NPC is a Rare Friend, including your wallet's other Friends. Moonlight
Blessings spend (simulated) $RAREFRIENDS on farm boosts and RF décor that makes nearby crops grow faster, and
**Friend Films** turn your farm into GIFs and videos with music to post.

## Screenshots

| Spring (camera rotated) | Autumn | Winter |
| --- | --- | --- |
| ![Spring](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-valley/main/docs/farm-rotated.png) | ![Autumn](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-valley/main/docs/farm-autumn.png) | ![Winter](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-valley/main/docs/farm-winter.png) |
| **Night on the farm** | **Town of Rare Friends** | **General Store** |
| ![Night](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-valley/main/docs/farm-night.png) | ![Town](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-valley/main/docs/town.png) | ![Store](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-valley/main/docs/store.png) |
| **Moonlight Blessing** | **RF décor collection** | **Clip ready to post** |
| ![Blessing](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-valley/main/docs/blessing.png) | ![Collection](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-valley/main/docs/collection.png) | ![Clip](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-valley/main/docs/clip-menu.png) |

**A clip recorded in-game (GIF with a slow camera orbit):**

![Animated clip recorded in the game](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-valley/main/docs/clip.gif)

## Wallet and network requirements

A browser wallet on **Robinhood mainnet (chain 4663)** holding a hardwired Rare Friends Generations NFT (generation ≥ 1).
FriendSDK's `GameHost` handles wallet connection, Friend selection and the fresh ownership check. Phones need a wallet with
an in-app browser (for example MetaMask Mobile). **All RF balances, purchases and rewards are simulated**: no contracts,
signatures or transactions.

## Setup and run

```sh
git clone https://github.com/M4S4T0-V01D/rarefriends-valley.git
cd rarefriends-valley
npm ci
npm run dev        # http://localhost:4173   (npm run dev:lan to play from a phone on the same network)
npm run build      # static site → games/rarefriends-valley/.friendsdk/
```

Node.js 22+. FriendSDK v0.1.2 is vendored as a tarball packed from the official `v0.1.2` tag.

## How to play

- **Farm:** clear weeds, rocks and stumps; till, plant and water. Tap the field with **Hands** and your Friend does what the tile needs, or pick the Hoe, Can, Seeds or Fertilizer (keys 1–5). Refill the can at the well or pond.
- **Grow:** crops grow one day per night when watered; rain and snow water them for you. Ten crops across four 7-day seasons; some regrow, and out-of-season crops wither.
- **Ship and shop:** the bin by your house pays out each morning. Walk the road east to **town**:
  - The General Store sells seasonal seeds, fertilizer, tool upgrades and décor.
  - The café sells food that restores energy.
  - The Moonlight Market sells RF blessings.
- **Energy (fatigue):** tools cost energy; tired Friends slow down; at 2 am you pass out (you wake tired and a little poorer). Eat or sleep.
- **Day/night:** a 6 am–2 am clock with dusk, glowing windows and lamps, and a night lullaby.
- **Villagers:** eight Rare Friend villagers keep schedules (work, socialising, sheltering from rain), talk daily and have favourite gifts and hearts. A notice-board request every morning. **Your other owned Friends move into town** and water your crops once they reach 3 hearts.
- **Camera:** rotate the 2.5D valley in quarter turns (Q / R or the buttons). WASD / arrows walk screen-relative; E acts; B bag; C clip.
- **Family perk:** Skeleton cheaper tools · Mask +10% prices · Family +25% friendship · Cellular seeds sometimes free · Asymmetry double harvests · Hoverer faster walking · Colossus +30 energy · Sparkling extra growth · Hollow double water.
- **Friend Films:** **● Clip** records the game as a looping GIF (its own encoder) and a video with the music (MP4 in Chrome/Safari, WebM in Firefox), to post to X or save. Every night draws a diary card to post. Posts are tagged @RareFriendsNFT #RareFriends #RareFriendsValley and link to https://rarefriends.com/.
- **Progress saves per wallet address** (on this device). Audio is procedural WebAudio: five seasonal and night tracks, including the café's Street Bossa, plus farm sounds.

### Moonlight Blessings: RF costs, odds and rules (simulated)

| Blessing | Chance | RF value | While kept | RF décor of this tier |
| --- | --- | --- | --- | --- |
| Sprout Charm | 60% (6,000 bps) | 0.5 RF | +1 Sprout Fertilizer charge each morning per charm (max 5) | Lucky Scarecrow, Wind Chime, Flower Arch |
| Silver Dew | 28% (2,800 bps) | 1 RF | Morning dew waters 4 crops per dew (max 12) | Crystal Sprinkler, Silver Beehive |
| Moon Bloom | 10% (1,000 bps) | 2 RF | Shipped goods sell +10% per bloom (max 30%) | Moon Lantern, Star Windmill |
| Golden Harvest | 2% (200 bps) | 5 RF | 8% of harvests turn golden (×3 price) | Golden Friend Statue |

- **Price** 1 RF (`1000000000000000000` base units); buy ×1 or ×5. **Expected RF value** 0.88 RF per blessing.
- **Consumable:** one blessing opens into exactly one outcome; single settlement, no reroll.
- **Backing:** each purchased or pending blessing reserves 5 RF; kept blessings keep their fixed RF backing, with no expiry. Redeeming removes that blessing's bonus.
- **RF décor:** every blessing also grants an uncollected RF-exclusive décor piece of its tier (or Gold for duplicates: 150/300/600/1,500). RF décor boosts crops in a radius (growth, watering, yield or golden chance), carries no RF value and is saved with your farm.

Blessings use the SDK chance-game client (`buy` / `play` / `settle` / `redeem`) with runtime confirmations. **Economy design:**
Gold is earn-only; RF is a boost, not a paywall; holding more Friends pays off as helpers. Proposed future RF integrations,
which need APIs beyond SDK v0.1.2: cloud saves, RF seed packs and cosmetics with burn, live Dice-RNG blessings, visiting
other holders' farms and trading crops, and tipping clips in RF.

### SDK integration notes

The runtime page is the SDK's `GameHost`, unchanged in behaviour. `host/runtime.tsx` adds three things:

1. A read-only `readOwnedFriends` roster (account-filtered, `eth_accounts` only), so owned Friends move into town.
2. Per-wallet `localStorage` saves, because the sandbox has no storage.
3. Sharing of the diary picture, clip GIFs and videos: the share sheet, or saving the file plus a prefilled X post, or clipboard. The sandbox can't download, open tabs or copy.

The sandboxed game receives the roster and save over `postMessage` from its parent window, and uses them only when the
roster contains the Friend the runtime just verified. There are no signatures or extra prompts.

### Credits

Scenery, buildings, crops, décor, icons, procedural villager Friends, the GIF encoder, and all music and sound effects
are original code. Your Friend and owned Friends use their canonical Generations sprites. Villagers Pip and Kumo use
canonical sample frames (#7730, #3412) from FriendSDK v0.1.2. UI cues use the FriendSDK sound kit. Rare Friends artwork
is used under the FriendSDK NOTICE. Gameplay inspired by farming life sims such as *Harvest Moon*; no assets from them
are used.

## Checks and known issues

| Check | Result |
| --- | --- |
| `npm run typecheck` (tsc strict, game + host + preview) | Pass |
| `npm test`: 25 unit tests (maps and routing, rotating camera, farming loop, regrowth and withering, weather, energy and passing out, shipping, shops and upgrades, RF décor boosts, blessings, villager schedules, gifts and hearts, owned-Friend helpers, requests, taps and travel, saves, roster, economy, GIF/LZW round-trips) | Pass |
| `npm run check` (`friendsdk check`) | Pass: expected reward 0.88 RF, max 5 RF |
| Browser, SDK CLI host, 960 px: a full day (walk, till, plant, water, hoe, rotate, bag, record a clip → GIF, travel to town, buy seeds and décor, open a blessing, place décor, sleep → diary → day 2, music picker) | Pass |
| Browser, 390 px touch: tap to walk, rotate, tools, hotbar fits | Pass |
| Browser, custom host, two-Friend mock wallet: #3412 moves in, clip GIF posted/saved through the host, video saved, diary card copied + X post, save and reload → restored | Pass |
| Browser, preview page: record player plays audibly on click and tap, and stops | Pass |
| All of the above in GitHub Actions before each Pages deploy | See the repo's Actions tab |
| Real-wallet playtest on Robinhood mainnet | By the builder (the build environment can't reach mainnet) |

Known limitations:

- Saves are per device and browser, keyed by wallet address, and client-side.
- Blessing balances and kept blessings reset on reload (SDK session ledger); RF décor persists.
- Video recording depends on the browser, and X doesn't take WebM, so on Firefox post the GIF. GIFs are silent.
- Villagers are procedural art in the Rare Friends style, except the SDK sample Friends and your own. The owned-Friend roster depends on the RPC returning the wallet's transfer history.
- Audio starts on the first tap; on iPhones before iOS 17, silent mode may keep it quiet.
- Wallet support is the SDK's (injected / EIP-6963).
- There is no wallet or fund risk: nothing is signed or sent.
