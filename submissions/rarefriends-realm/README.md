# RareFriends Realm

**▶ Play:** https://m4s4t0-v01d.github.io/rarefriends-realm/ · **Preview page:** https://m4s4t0-v01d.github.io/rarefriends-realm/preview/ · **Source:** https://github.com/M4S4T0-V01D/rarefriends-realm

*An old-school adventure starring the Rare Friend you own: nineteen skills, six quests, a large 2.5D world and a Hollow King to end.*

![RareFriends Realm: Friendhollow square in greyscale isometric, with Rare Friends, a fountain and the minimap](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-realm/main/docs/town.png)

| | |
| --- | --- |
| **Project** | RareFriends Realm |
| **Builder** | M4S4T0 · GitHub [@M4S4T0-V01D](https://github.com/M4S4T0-V01D) |
| **Category** | Character Spotlight (also entering Economy Potential and Token Activity) |
| **Source repository** | https://github.com/M4S4T0-V01D/rarefriends-realm |
| **Playable preview** | https://m4s4t0-v01d.github.io/rarefriends-realm/ (GitHub Pages, deployed by CI from `main`) |
| **Preview page** | https://m4s4t0-v01d.github.io/rarefriends-realm/preview/ (screenshots, regions, quests, casket odds, and a jukebox of all 18 music tracks) |
| **Stack** | FriendSDK **v0.1.2** (SDK `GameHost` + CLI game build), React 19, Canvas 2D, WebAudio, TypeScript |

**One sentence:** A tick-based, old-school browser RPG where your verified Rare Friend is the hero, drawn from its
canonical on-chain sprite with a family perk. You right-click your way through a 240 × 240 tile island, training nineteen
skills and finishing six quests, while your other owned Friends follow you for bonus XP. Rare Caskets spend (simulated)
$RAREFRIENDS on kept-or-redeemed relics and wardrobe pieces.

## Screenshots

| Title screen | Right-click menus | Talking to the Realm Guide |
| --- | --- | --- |
| ![Title](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-realm/main/docs/title.png) | ![Menu](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-realm/main/docs/menu.png) | ![Dialogue](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-realm/main/docs/dialogue.png) |
| **Fighting Grumblins** | **Emberforge** | **Frostpeak** |
| ![Combat](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-realm/main/docs/combat.png) | ![Emberforge](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-realm/main/docs/region-emberforge.png) | ![Frostpeak](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-realm/main/docs/region-frostpeak.png) |
| **The Hollow King** | **World map** | **Rare Caskets** |
| ![Boss](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-realm/main/docs/region-throne.png) | ![Map](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-realm/main/docs/worldmap.png) | ![Caskets](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-realm/main/docs/caskets.png) |

**Adventurer card, ready to post on X:**

![Adventurer card](https://raw.githubusercontent.com/M4S4T0-V01D/rarefriends-realm/main/docs/adventurer-card.png)

## Wallet and network requirements

A browser wallet on **Robinhood mainnet (chain 4663)** holding a hardwired Rare Friends Generations NFT (generation ≥ 1).
FriendSDK's `GameHost` handles wallet connection, Friend selection and the fresh ownership check. Phones need a wallet with
an in-app browser (for example MetaMask Mobile); play in landscape. **All RF balances, purchases and rewards are simulated**:
no contracts, signatures or transactions.

## Setup and run

```sh
git clone https://github.com/M4S4T0-V01D/rarefriends-realm.git
cd rarefriends-realm
npm ci
npm run dev        # http://localhost:4173   (npm run dev:lan to play from a phone on the same network)
npm run build      # static site → games/rarefriends-realm/.friendsdk/
```

Node.js 22+. FriendSDK v0.1.2 is vendored as a tarball packed from the official `v0.1.2` tag.

## How to play

- **Controls:** left-click does the first option (shown top-left); right-click or long-press lists every option (*Chop down*, *Attack Grumblin (level-5)*, *Talk-to*, *Pickpocket*, *Examine*…), in the world and in every interface (bank, shops, spellbook, prayers, equipment, production, compass, minimap). WASD walks; ← → turn and ↑ ↓ tilt the camera (or drag with the scroll wheel held), and the compass turns north to the top of the screen. R toggles run, scroll zooms, M opens the world map, the minimap walks you anywhere. Every monster shows a health bar and its level. F1–F9 switch tabs; Space and 1–5 drive dialogue.
- **The tick:** everything runs on a 0.6 s game tick. You walk one tile per tick (two when running, two or three on a mount).
- **Skills (19), old-school XP curve at a Realm rate of ×3:** Attack, Strength, Defence, Ranged, Hitpoints, Magic, Prayer, Sigilcraft, Woodcutting, Fletching, Fishing, Cooking, Firemaking, Mining, Smithing, Crafting, Thieving, Agility, Slayer. Gathering rolls, burn chances, accuracy and max hits follow the classic formulas.
- **Ranged:** bows by wood (Shortbow to Ashwood, plus the Gloomfang bow) fire the best arrows in your pack (pewter to rarite), with Accurate, Rapid and Longrange styles; most arrows can be picked up again.
- **Slayer:** Warden Thistle gives kill tasks, each kill on task pays Slayer XP, and finished tasks pay points for her rewards (the Warden's helm, the Gloomfang bow, lamps). Mire crawlers, frost wisps and gloom hounds can only be wounded at Slayer 10, 30 and 50.
- **Play together:** everyone online shares the Realm. You see other players' Friends walk around in their wardrobes and capes, chat in public (bubbles over their heads) or whisper (`@1234 hello`), and right-click a player to *Follow*, *Trade with*, *Add-friend*, *Message*, *Wave*, *Ignore* or *Examine*. Players fight the same monsters together (both players' hits count; each other's health bars show), trade items old-school style (offer screen, then a confirm screen, swapped only when both games agree), see and take each other's dropped items, and perform 14 emotes the others see. A friends list shows who's online and where; friends nearby add +5% XP. The sandboxed game never touches the network: the trusted host page connects players peer to peer (WebRTC via Trystero, introduced over public Nostr relays, no server), shares only Friend IDs (never wallet addresses), validates and rate-limits everything received, and strips links from chat. Each player's monsters and drops stay their own.
- **Magic that looks like magic:** spells fly as glowing comets by element with sparks and impact bursts, staffs are held upright, and at night and in (now dark) dungeons spells, arrows, dragonfire and torches light the ground.
- **Skill guides and a recipe book:** click any skill for what it unlocks at each level; a recipe book lists every recipe. Also on the site: https://m4s4t0-v01d.github.io/rarefriends-realm/preview/guides.html
- **Save codes:** Settings → Copy save code / Download save file puts your whole adventure in one line of text, restorable on any browser with the same Friend.
- **Fletching and Sigilcraft:** a knife turns logs into arrow shafts or bows, feathers and anvil-smithed arrowheads finish the arrows; sigil stones mined in the Wizards' Tower are pressed into sigils at eleven altars across the Realm. Archmage Solenne starts every Friend in magic (robes, a staff, sigils), sigils are cheap, and elemental staffs stand in for them.
- **Dragons:** Wyrmreach's ash drakes, cinder drakes and Old Cinder (level 148). A third of their attacks are dragonfire, which only King Hollis's Wyrmward shield turns aside; drakehide makes archer's armour.
- **Gold making:** merchants pay 55–70% for their own trade (fish, logs, ore and bars, sigils, hides and bones, gems, bows and arrows) instead of 40%.
- **Mastery capes:** reach 99 and the Keeper of Capes sells that skill's cape (99,000 coins); master two skills and they come trimmed, master all 17 for the Grandmaster's cape. Capes are worn on your Friend's sprite.
- **Use items on things:** raw food on a range or fire, tinderbox on logs, ore at the furnace, bars at the anvil, needle on leather, chisel on a gem.
- **Combat:** four styles, food, prayers (Paper Shield … Friend's Ward), a 26-spell book paid in sigils: Darts, Lances and Bursts, the curses Muddle, Wilt and Brittle, Rootsnare, Gilded and Golden Touch, Forgeheart, Far Reach, Bonebloom, two enchantments and six ways to travel (staffs autocast damage spells). Monsters retaliate, some attack on sight, all drop loot. Death is safe: you keep your items.
- **Quests (9 quest points):** A Friend's Feast, Grumblin Trouble, The Cold Forge, Hollow Whispers, The Lost Glimmer, and The Hollow King (level 92 boss).
- **Real buildings, in pixel art:** half-timbered plaster houses and stone keeps, textured in the same chunky pixels as the trees and rocks, with leaded windows, shingle roofs and smoking chimneys; a roof lifts away as you walk in, walls in front of you drop to a cutaway, and a roof fades whenever it would hide you.
- **Friendhollow:** the fountain square, the bank, the chapel, Market Street (Hollis Armoury, Edge & Hilt, Fletch & Feather, the Warden's Lodge), the Sleepy Friend inn, the Rare Market, and Friendhollow Castle: three storeys with spiral stairs up to King Hollis's throne room and the battlements.
- **Day and night:** a 24-minute day with warm dusks and dark nights. Light pools on the ground around lamps, torches and fires (which flicker) and your own dim light. The minimap is clearer and colour-coded.
- **Weather everyone shares:** the sky follows the real clock in four-minute spells, so every player sees the same weather at once. It can be clear, rainy, or a storm with lightning, thunder after the flash and a darker sky. Dawn brings ground fog, the Murkmire is always misty, and deserts and peaks stay dry.
- **The Friendhollow stables:** eight mounts for RF: chestnut, piebald, bay, dapple grey, palomino and black warhorse, plus a rainbow-maned unicorn and a moonlit unicorn. Riding carries you two or three tiles a tick without run energy, and each mount has a gift: healing, faster gathering, more coins, Defence, XP or light in the dark. Horses and a unicorn graze in the paddock, and other players see you riding.
- **Gear you can see:** helms, hats, shields and weapons are painted into your Friend's own pixels. Blades sit in a ready guard, staffs stand upright with their orb, bows are held by the grip and axes rest on the shoulder. They rock with your step and swing free only mid-attack.
- **Referral codes:** every Friend has a code (`RF-<Friend #>`). Both players get +15% XP for an hour of play and 250 coins, and your first referral earns a Friendship cape with its own emote.
- **Selling:** general stores in four towns buy almost anything, every trader buys back what it sells, and what you sell sits on the shelf to buy back.
- **Pixel ground:** grass tufts with the odd flower, pebbled paths, cobbled streets, flagstones and rippled sand in the buildings' texture style. Furnaces are brick kilns with fire in the mouth, and campfires burn on a pile of cut logs.
- **Sound everywhere:** weapon swings, a voice for every creature (attack, hurt, death, aggro, idle), axes and picks on the beat, NPC speech blips, footsteps by ground, crackling fires, forge, water and regional wildlife.
- **A living world:** walkable rolling hills lit by slope and traced with ink contours; cloud shadows, birds, butterflies, falling leaves, snow, dune dust, fireflies, jumping fish and forge smoke.
- **Pixel art and animation:** trees, rocks, decor, every item, weapon and icon are pixel art with an ink edge like the canonical Friends; skills animate (axe swings and wood chips, pickaxe sparks, cast lines, anvil sparks, cooking steam, agility hops) and weapons swing.
- **World:** 14 regions (the Wizards' Tower and Wyrmreach, Friendhollow, Hollow Farms, Whisperwood, Ashen Hills, Emberforge, Frostpeak, Glass Lake, Pale Dunes, Oasis, Murkmire, Mossy Ruins, the Pale Coast) and 2 dungeons (Murkmire Crypt, Hollow Depths), with banks, shops, an agility course and market stalls.
- **Family perk:** Skeleton (+50% Prayer XP from bones) · Mask (better Thieving) · Family (shops 10% cheaper) · Cellular (HP regenerates 2× faster) · Asymmetry (8% chance of a second resource) · Hoverer (run drains 40% slower) · Colossus (+1 melee max hit) · Sparkling (gems 3× as often) · Hollow (+10% magic accuracy, 1 in 5 spells keeps its sigils).
- **Followers:** your other owned Friends walk the tiles you leave behind like an old-school pet, drawn with their canonical art: Gen 1 +5% XP … Gen 5+ +1%.
- **Audio:** 18 procedural tracks in an old-school MIDI style (recorder, oboe, trumpet, harp, pizzicato strings, glockenspiel, timpani): a main theme and one per region, dungeon and boss, plus level-up and quest fanfares. Entering an area unlocks its track; the music player in Settings replays any you've found. Music and effects have their own volumes.
- **Saves:** progress saves automatically for your wallet and Friend on this device. The adventurer card can be posted to X, tagged @RareFriendsNFT #RareFriends #RareFriendsRealm.

Full rules, levels, monsters and controls: [games/rarefriends-realm/README.md](https://github.com/M4S4T0-V01D/rarefriends-realm/blob/main/games/rarefriends-realm/README.md).

### Rare Caskets: RF costs, odds and rules (simulated)

| Relic | Chance | RF value | Kept bonus | RF-exclusive wardrobe |
| --- | --- | --- | --- | --- |
| Plain Relic | 60% (6,000 bps) | 0.5 RF | +2% XP in every skill per relic (max 5) | Rose cape, Sage scarf, Paper crown, Butter bow |
| Silver Relic | 28% (2,800 bps) | 1 RF | +10% coins from drops and pickpockets per relic (max 3) | Silver halo, Moonblue cape, Lantern familiar |
| Moonlit Relic | 10% (1,000 bps) | 2 RF | Gather 10% faster per relic (max 3) | Moon wisps, Starlit hood, Ink wings |
| Golden Relic | 2% (200 bps) | 5 RF | +10% XP and a golden aura while kept | Golden aura, Rarite crown |

- **Price** 1 RF (`1000000000000000000` base units); buy ×1 or ×5. **Expected RF value** 0.88 RF per casket; top prize 5 RF.
- **Consumable:** one casket opens into exactly one relic; single settlement, no reroll.
- **Backing:** each purchased or pending casket reserves 5 RF; kept relics keep their fixed RF backing, with no expiry. Redeeming removes that relic's bonus.
- **Wardrobe:** every casket also grants an uncollected piece of its tier (12 in all), painted into your Friend's own sprite so it sits on the real head, shoulders and neck, or coins for duplicates (250/600/1,500/5,000). Wardrobe pieces carry no RF value and are saved with your adventure.

**The Rare Market:** traders in Friendhollow, Emberforge, the Oasis, Frostpeak, Pike's Pier, the Wizards' Tower and the
Wyrmreach camp (each by a casket chest) sell nine bundles. RF buys one thing in the SDK's economy, the Rare Casket, so every bundle buys caskets and adds guaranteed goods:
Realm tablets (1 RF), a hero's hamper (1 RF), a Lamp of insight (2 RF), 40 Slayer points (2 RF), an archer's quiver
(2 RF), a sigil sack (1 RF), a fletcher's crate (1 RF), a dragonslayer's kit (3 RF), or the wardrobe piece of your choice (3 RF).

Caskets use the SDK chance-game client (`buy` / `play` / `settle` / `redeem`) with runtime confirmations. **Economy design:**
coins are earn-only and never convert to RF; RF is a boost, not a paywall; holding more (and better-generation) Friends
pays off as followers. Proposed future RF integrations, which need APIs beyond SDK v0.1.2: cloud saves, a holder-to-holder
trading post, RF-priced cosmetics with burn, live Dice-RNG caskets, and boss leaderboards.

### SDK integration notes

The runtime page is the SDK's `GameHost`, unchanged in behaviour, in a 16:9 frame set through the SDK's documented
layout variables (`host.css`). `host/runtime.tsx` adds three things. First, a read-only `readOwnedFriends` roster with
generations (account-filtered, `eth_accounts` only, retried on RPC rate limits). Second, `localStorage` saves keyed by wallet
and Friend, because the sandbox has no storage. Third, adventurer-card sharing (share sheet, or clipboard plus a prefilled
X post), because the sandbox can't open tabs or copy. The sandboxed game receives the roster and save over `postMessage`
from its parent window, uses them only when the roster contains the Friend the runtime just verified, and validates every
field of a save on load. There are no signatures or extra prompts.

### Credits

The world, creatures, townsfolk Friends, item art, music and sound effects are original procedural code. Your Friend and
your followers use their canonical Generations sprites; Old Glimmer (#7730) and Brother Ossic (#3412) use the canonical
sample frames from FriendSDK v0.1.2. Rare Friends artwork is used under the FriendSDK NOTICE. Gameplay is inspired by
classic browser RPGs such as *Old School RuneScape*; the Realm's places, metals, gems, sigils, spells, prayers and items have their own names, and no assets or code from it are used.

## Checks and known issues

| Check | Result |
| --- | --- |
| `npm run typecheck` (tsc strict: game, host, preview page) | Pass |
| `npm test`: 37 engine tests (Fletching; Sigilcraft; dragonfire and the Wyrmward shield; merchants and the Archmage; Ranged; Slayer tasks, points and Slayer-only creatures; mastery capes; Rare Market bundles, tablets and lamps; the castle stairs; XP curve; world determinism and on-foot reachability of every station, rock, spot, ladder, NPC and the boss; pathfinding; WASD; menus; woodcutting, firemaking, cooking; fishing; mining, smelting, smithing; combat, loot, aggression, safe death; A Friend's Feast and Grumblin Trouble end to end; thieving; an agility lap; magic; prayer; shops and bank; magic utility spells and Rootsnare; saves incl. tampering and pre-rename ids; caskets; followers; music unlocks) | Pass |
| `npm run check` (`friendsdk check`) | Pass: expected reward 0.88 RF, max 5 RF |
| Browser, custom host, two-Friend mock wallet (1280 px): title screen; real mouse click chops a tree; right-click menu; dialogue; WASD; chat over your head; camera turn/tilt by arrow keys and middle-drag, WASD at an angle, compass turns north; a level-up; smelting; a shop; finishing A Friend's Feast; combat by right-click; bank; world map; 5 caskets through the runtime's confirmations; a Rare Market bundle from a trader; right-click inside the bank; two players in two tabs seeing each other, chatting, whispering, adding a friend, an emote, taking a dropped item and a full trade by clicks; a shared fight; the castle's spiral stairs by real clicks; nightfall; adventurer card → Post to X (prefilled + picture copied); a follower; a 14-region tour; save written and restored after reload | Pass |
| Browser, phone in landscape (844 × 390, touch): tap to walk | Pass |
| Browser, preview page: the main theme and a jukebox track play audibly on desktop and phone, and stop | Pass |
| All of the above in GitHub Actions before each Pages deploy | Pass |
| Real-wallet playtest on Robinhood mainnet | By the builder (the build environment can't reach mainnet) |

Known limitations: saves are per device and browser, keyed by wallet and Friend, and client-side. Casket balances and
kept relics reset on reload (SDK session ledger); wardrobe pieces persist. The Realm is single-player (other players and
trading need cross-player APIs). Audio starts on the first tap; on iPhones before iOS 17, silent mode may keep it quiet.
Wallet support is the SDK's (injected / EIP-6963). There is no wallet or fund risk: nothing is signed or sent.
