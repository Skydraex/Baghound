<div align="center">

# Baghound

### Built and maintained by [Skydraex](https://github.com/Skydraex)

<img width="1080" height="1920" alt="Image" src="https://github.com/user-attachments/assets/e6c37ad4-a8ea-4794-8c2f-8eda3aaf53ca" />

</div>

**Baghound** is a loot & DPS companion for **Realm of the Mad God Exalt** — a
stable, read-only packet sniffer that tracks your DPS, loot drops, collection,
fame, chat and quests in real time, wrapped in a clean pixel-art interface.

It began as a hardened fork of
[RealmShark](https://github.com/X-com/RealmShark) +
[Tomato](https://github.com/X-com/RealmShark/tree/tomato) — the MIT-licensed
projects that do the core sniffing work — and grew into its own application:
**Baghound**. It keeps every upstream feature, fixes the bug that makes
upstream stop capturing after about 30 seconds, and adds a large set of
original features on top:

- **A pixel-art interface** — every screen built in a crisp retro style, with
  **five live-switchable themes** (Dark, Light, Midnight, Ember, Purp).
- **A detailed DPS logger** — a live per-player leaderboard with damage dealt,
  damage taken, projectile hit %, and the HP each player nexused at, plus a
  full saved history of every past boss.
- **Statistics tracking** — your fame over time as a per-character graph, a
  per-day fame table, and a Dungeon Stats screen that features your most-run
  dungeons.
- **A collection log** — a permanent record of every notable item you've seen
  drop, a live "still-owned" view with automatic dismantle/loss detection, and
  shareable text / image export.
- **Loot drops posted to Discord** — your best drops, as a clean ROTMG-styled
  image card, to any number of channels.
- **A RealmShark bot bridge** — feed guild loot tracking / PPE / seasonal
  competitions ("Loot Goblin").
- **In-app updates** — checks for new builds in the background and installs
  them in a couple of clicks, all from the status bar — no pop-ups.

> **EULA-safe.** A read-only network sniffer — no packet injection, no game
> files shipped or modified. Same compliance posture as upstream RealmShark.

**Like the tool?** You can [support development on GitHub Sponsors](https://github.com/sponsors/Skydraex)
— completely optional, and Baghound stays free to use either way.

---

## Why Baghound?

RealmShark and Tomato are great projects — Baghound smooths off the rough
edges and keeps everything you'd want in one place:

- **It doesn't stop after ~30 seconds.** Upstream has a long-standing capture
  bug that quietly halts on longer sessions. Baghound fixes it, so capture
  lasts as long as you're playing. (Details in
  [What this build adds](#what-this-build-adds).)
- **Latest features *and* guild bridging, together.** Newer upstream builds
  dropped the loot-bridge settings — so anyone feeding a guild tracker
  (Loot Goblin / PPE / seasonal) was stuck on an old version, missing newer
  features. Here the RealmShark bot bridge is built in *and* kept current.
- **It keeps itself current on its own.** Upstream improvements are merged in
  automatically every week, so the base never goes stale — with nothing for
  you to do.
- **Updating is safe.** Every version is kept as a permanent download, so if a
  build ever misbehaves you can roll straight back (see
  [Older versions & downgrading](#older-versions--downgrading)).
- **And it tracks more.** A detailed DPS logger, a Statistics tab, a
  persistent collection log, Discord loot cards — all wrapped in a full
  pixel-art interface. See [How Baghound compares](#how-baghound-compares).

Nothing here changes how the game is played — it's the same read-only sniffer.
It just stays running, stays current, and keeps your guild bridge working.

---

## How Baghound compares

Stock **Tomato** — the upstream release Baghound tracks — does the core
sniffing well, but it ships as a bare `.jar`, has a capture bug on long
sessions, and has no loot-sharing, collection or statistics tooling. Baghound
keeps the **entire** upstream feature set and builds a full application around
it.

### Reliability

| | Stock Tomato | Baghound |
|---|---|---|
| Core sniffing — DPS, loot, chat, quests | yes | yes — kept, and synced from upstream weekly |
| Capture survives long sessions | stops after ~30s | fixed — two concurrency bugs replaced |
| Loot tab fills from the first dungeon | only after a reconnect | fixed |
| Crash hardening — desync, bad packets, out-of-memory | — | guarded throughout the pipeline |
| Packet IDs kept current after Deca patches | manual | fetched live from the Crucible API on launch |
| Game assets — items, enemies, sprites | manual | extracted live from your install on launch |

### Interface

| | Stock Tomato | Baghound |
|---|---|---|
| Visual style | older theme | full pixel-art redesign, every screen |
| Themes | one | five, switchable live — Dark, Light, Midnight, Ember, Purp |
| Tab bar | fixed | drag-to-reorder, order saved per machine |
| Settings | scattered menus | one Settings tab; saved per-user, survive updates |
| First-run Npcap check | — | guided onboarding |

### Tracking & stats

| | Stock Tomato | Baghound |
|---|---|---|
| DPS readout | damage dealt only | live leaderboard + per-player damage taken + nexus HP% |
| Per-boss history | — | every run saved locally, browse any time |
| Leaderboard export | — | copy as text or as an image card |
| Fame tracking | — | per-character fame graph — 7 / 30 / 90-day and all-time |
| Daily fame breakdown | — | per-day fame table |
| Dungeon stats | — | most-run podium with boss sprites, peak + previous-peak DPS |

### Collection & sharing

| | Stock Tomato | Baghound |
|---|---|---|
| Collection log | — | lifetime grid, dated log, All / Shiny / Normal filter |
| Live "still-owned" collection | — | auto dismantle / death / loss detection, vault self-correction |
| Hand-correcting the collection | — | click + arrow editing on both grids |
| Collection export | — | copy as text or as an image |
| Loot drops to Discord | — | rendered ROTMG-style image cards |
| Multi-channel posting | — | post every drop to any number of webhooks at once |
| Guild loot bridge — Loot Goblin / PPE / seasonal | dropped from recent builds | built in and kept current |

### Delivery

| | Stock Tomato | Baghound |
|---|---|---|
| Download | bare `.jar` + manual JDK 21 | one-click Windows `.exe`, bundled Java runtime |
| Updating | manual re-download | background check + no-pop-up status-bar self-update |
| Older versions | — | every version kept as a permanent downloadable archive |
| Builds & releases | manual | automated CI, with weekly upstream sync |

**Compared with other ROTMG sniffers**, the goal is a build that doesn't go
stale *and* tracks more than the rest. Most sniffers are RealmShark-based and
drift out of date as Deca patches the game; Baghound resyncs with upstream
every week, fetches packet and asset changes live on launch, and updates
itself — while staying a strictly read-only, EULA-safe sniffer (no packet
injection, no game files modified). On top of that it goes far deeper than a
stock sniffer: a combat log that keeps a full per-boss history, a Statistics
tab that charts your fame and ranks your dungeons, a persistent collection log
that knows what you still own, Discord loot cards, a guild bridge, and a
five-theme pixel interface — all original to Baghound.

---

## Install (Windows)

You need three things. **Do them in order.**

### 1. Install Npcap

Download from <https://npcap.com> and run the installer. **Important:** when
the installer asks, **tick the "WinPcap API-compatible mode" checkbox**.
Without it Baghound can't read network traffic.

### 2. Have ROTMG Exalt installed

Baghound reads its item / enemy / projectile database from your local ROTMG
client on first launch. If you can play the game, you have what you need.

### 3. Download and run Baghound

1. Go to the [**latest release**](https://github.com/Skydraex/ROTMG-packet-sniffer/releases/tag/latest)
   and download `Baghound-windows.zip` from the **Assets** section.
   (If you see "no releases yet" or a 404, CI hasn't finished its first
   build — check the
   [Actions tab](https://github.com/Skydraex/ROTMG-packet-sniffer/actions)
   and wait for the green check.)
2. Unzip it anywhere (Desktop is fine).
3. Open the unzipped `Baghound` folder and **double-click `Baghound.exe`**.

> No separate Java install needed — the bundle ships its own Java runtime.

### Why a `.exe` and not a `.jar`?

A plain `.jar` would force every user to first install a matching Java
runtime (JDK 21) and launch the tool from the command line — a real hurdle
for most players and a constant source of "wrong Java version" problems.

The `.exe` is built with `jpackage`: it bundles its **own private Java
runtime**, so it just double-clicks and runs, with nothing else to install
and no version conflicts. It is a normal Windows app, not a command-line one.

---

## First run

1. Launch ROTMG Exalt.
2. Launch `Baghound.exe` (either order is fine).
3. Click the **Start Sniffer** button at the bottom-right of the window.
4. Join a dungeon. The **DPS Logger**, **Loot** and **Chat** screens populate
   live.

On first launch Baghound takes a few seconds to extract assets from your
ROTMG install. This is normal and only happens once per game patch.

The status bar along the bottom shows whether capture is running, the build
identifier (handy when reporting an issue), and the update control.

---

## The interface

Every screen is built in Baghound's own pixel-art style — custom panels,
tables, charts and controls, consistent end to end. The screens sit behind a
tab bar you can **drag to reorder**; your chosen order is saved per-machine.

### Themes

Baghound ships **five themes**, switchable from **Settings → Theme**:

- **Dark** — the charcoal-and-gold default.
- **Light** — a warm-paper light theme.
- **Midnight** — deep indigo with a cyan accent.
- **Ember** — dark and warm with a glowing orange accent.
- **Purp** — deep violet with a bright purple accent.

Themes **apply instantly** — pick one and the whole interface recolours on the
spot, no restart needed.

---

## DPS logger

The **DPS Logger** is a full damage breakdown for every boss you fight — live
as it happens, and saved afterwards.

![DPS Logger](https://github.com/user-attachments/assets/ee2e9bfd-0969-43fe-95a1-2aaded2648ac)

- **Live leaderboard** — every player in the fight ranked by DPS, with total
  damage dealt and their share of the boss's HP.
- **Damage taken** — how much damage each player took during the fight,
  racking up live alongside the damage they dealt.
- **Nexus HP%** — when a player nexuses out, the exact HP% they escaped at is
  shown next to their name.
- **Per-boss history** — every run is saved locally, so you can scroll back
  through past dungeons and bosses long after the session has ended.
- **Shareable exports** — copy any boss leaderboard as text, or as a clean
  image card, straight to your clipboard.

This is a far deeper combat log than a stock sniffer's damage-only readout —
the whole picture of a run, per player, in one table.

---

## Chat log

The **Chat** tab is a unified chat window for every message Baghound sees in
the game — public, party, guild and PMs — all in one scrollable feed.

![Chat log](https://github.com/user-attachments/assets/961e2cfb-1f3a-4682-bcc0-4e7b79d0e198)

- **Channel filters** — toggle Guild / Party / PM / Public on the right to
  narrow the feed to just the conversations you care about.
- **Clear Chat** — a button at the top of the panel wipes the visible log to
  start a fresh slate.
- **Read-only** — Baghound can only see chat; it never sends messages. As with
  the rest of the sniffer, no packet injection.

---

## Statistics

The **Statistics** tab turns your tracked play into readable history.

![Dungeon Stats](https://github.com/user-attachments/assets/8a7b5d83-757b-4427-a619-5357b1373b42)
![Fame graph](https://github.com/user-attachments/assets/0bf61648-f321-4485-a06a-937ea1591359)

- **Fame Graph** — your fame over time as an area chart, with 7-day, 30-day,
  90-day and all-time ranges, plus headline tiles for fame gained, best day,
  daily average and current streak. The graph is **per character** — it
  always tracks the character you're playing, and switching characters never
  blends their fame together.
- **Fame Table** — a per-day breakdown: fame gained, dungeons run, and your
  best single run that day.
- **Loot** — your logged loot drops.
- **Dungeon Stats** — your dungeons ranked by how often you've run them. Your
  most-run dungeon is **featured at the top with its boss sprite**; the second
  and third sit beside it; the rest follow in a table. Each dungeon also shows
  your peak DPS — and your previous peak, so you can see your record improve.

---

## Collection log

![Collection log](https://github.com/user-attachments/assets/10cfba56-e65a-4d7d-9f06-46ef01b5065b)

The **Collection** tab keeps a permanent record of every notable ("top") item
the sniffer has seen drop — across every session, stored locally so it
survives updates. Items are recorded the moment a bag drops; you don't have to
pick anything up. The same "tops" filter the Discord posting uses decides what
counts (see [What posts to Discord](#what-posts-to-discord)).

- **Grid** — every top item in a fixed grid; the ones you've collected are lit,
  the rest dimmed, so it fills in as you play. A filter switches between
  **All**, **Shiny** and **Normal**. Click an item, then use the on-cell
  arrows or Up/Down keys to adjust its count by hand.
- **Live** — a second grid that tracks only the items you *still own*. When a
  character dies, or an item is dropped, disenchanted, dismantled, fed to a pet
  or traded away, it dims out here — while your lifetime **Grid** stays
  complete forever. The live grid is editable too, and it **self-corrects**:
  anything it can see in your vault is restored automatically, so a
  mis-detected loss never sticks.
- **Log** — a dated list with per-item counts. Shiny items are marked, since a
  shiny and its normal version share the same name.
- **Copy as text / Copy as image** — export your collection to share; the
  export follows whichever grid filter (All / Shiny / Normal) is selected.
- **Skin history** — your character skin history auto-imports on first
  launch, so the grid isn't blank when you start. Pet skins are honour-based
  (added by hand) since they aren't publicly listed anywhere.

---

## Your profile on baghound.app

Sign into [**baghound.app**](https://baghound.app) and the sniffer syncs your
collection, characters, DPS history, fame and dungeon stats to a shareable
profile page. Friends and guildmates can view your collection grid, fame
graph and past dungeon runs without you sending screenshots around.

- **Free** accounts get a **2-week Pro trial** on signup — full access to
  everything while you try it out.
- After the trial you keep a free tier (your profile stays public, recent
  runs and a count-only collection summary remain visible); Pro unlocks
  the full DPS history, collection grid, fame breakdowns and more.
- Account linking is via the sniffer's **License** tab — there is no
  separate password to manage.

---

## Loot drops to Discord

![Discord webhooks](https://github.com/user-attachments/assets/2c573562-6b7b-45c7-bfb5-edff39283668)

Baghound posts your best loot drops to a Discord channel as a clean,
ROTMG-styled image card. It is read-only and per-user — nothing posts until
you connect your own webhook (see **Setup** below).

### What posts to Discord

Only **"tops"** are posted — the loot Realm players actually care about. A
drop is posted if it is:

- a **UT** (untiered) item
- an **ST** (set) item
- a **ring** or **ability** of **tier 7 or above**
- **armour** or a **weapon** of **tier 14 or above**
- a **skin** or **pet skin**

Everything else — consumables (potions, marks), low-tier gear — is ignored.
The filter runs **per item**, so even a white bag only posts the tops inside
it, not its filler. (Sprite Wand is excluded by name.)

### What each card shows

<img src="https://github.com/user-attachments/assets/c5b38075-737d-45ed-a1ff-417f34f1e189" width="440" alt="Discord loot card">

Each posted drop becomes one image card with a row per item. Every row shows:

- the item's **actual in-game sprite**, black-outlined like the game
- a **coloured border** that encodes the enchant count — green (1), blue (2),
  purple (3), gold (4)
- one **diamond per enchant** along the sprite's bottom-left (1-4)
- **twinkling sparkles** scattered around the sprite if the item is **shiny**
- the **rarity** — Uncommon / Rare / Legendary / Divine — from the enchant
  count (Divine = 4 enchants)
- **type, tier (or UT/ST), Soulbound, damage, on-equip stats, MP cost, feed
  power, XP bonus** and the item's description — all pulled from the game's
  own data

It posts **once per bag** — running off a bag and back onto it will not
repost it.

> The **Discord** tab also has a **Send Test Loot** button. It posts a sample
> card covering each enchant tier and a shiny item, so you can see exactly
> what real drops will look like in your channel before you ever get one.

### Setup (each user picks their own channels)

Every user configures their own channels — nothing is hard-coded, so a fresh
download posts nowhere until you set it up. No Discord bot needed.

1. **Create a webhook.** In Discord, open the channel you want drops posted
   to → **Edit Channel → Integrations → Webhooks → New Webhook** →
   **Copy Webhook URL**.
2. **Paste it into Baghound.** Open the **Discord** tab, paste the webhook
   URL into a row, optionally give it a name (e.g. your server's name), and
   click **Save**.
3. **Add more if you like.** Click **+ Add another webhook** for each extra
   channel — every drop is posted to all of them at once.

Once saved, a row collapses to a status line showing the connection and the
webhook's name; the URL itself is hidden. Each row has **Edit** (change the URL
or name), **Copy webhook link** (copy the URL to share), and **✕** (remove).
The list persists between launches.

> Discord's API only exposes the *webhook's* own name, not the server or
> channel name — that's why you can give each webhook your own label.

### Notes

- Paste the **webhook URL** (`https://discord.com/api/webhooks/...`), not the
  channel link from your browser — they are different things.
- The URL is saved locally on your PC and is never uploaded anywhere.
- Treat the webhook URL like a password — anyone who has it can post to that
  channel. To share one loot channel with friends, give them the same webhook
  URL to paste into their own copy.

---

## RealmShark bot bridge (Loot Goblin / PPE / seasonal)

Separately from the Discord webhook above, Baghound can feed the **RealmShark
loot bot** ("Loot Goblin") — guild loot tracking, PPE vs seasonal,
competitions. This connects to each player's *existing* RealmShark data; it is
not a fresh tracker of our own.

Open the **Bridge Review** tab and fill in the **Bridge Settings**:

- **Endpoint** — the RealmShark ingest URL
- **Guild ID** — your guild's id
- **Link Token** — the token from RealmShark's `/mysniffer` command
- **CSV Path** *(optional)* — the tracked-items list
- Tick **Enabled**, then **Save Bridge Settings**

You get the endpoint, guild id, and link token from RealmShark's bot/Discord
(`/mysniffer → Configure Characters`). The **Bridge Logs** tab shows live
bridge activity; the Bridge Review tab also lists which drops were sent vs.
skipped.

---

## Settings

![Settings](https://github.com/user-attachments/assets/f8f8ff57-9095-4da7-9457-6a9250a60b97)

The **Settings** tab gathers every option in one place:

- **Sound & Pings** — a volume slider plus toggles for chat pings (PM, party,
  guild) and loot-bag pings (white, orange, red, gold, egg, blue, trade).
- **Loot Filter** — which loot-bag colours appear in the loot logger.
- **Theme** — the live theme picker (see [Themes](#themes)).

The **Chat** tab has its own **Clear Chat** button, and settings are saved
per-user so they carry across updates and re-downloads.

---

## Staying up to date

**As a user, you don't have to do anything.** Baghound keeps itself current
automatically:

- **New items, enemies, sprites** — pulled live from your ROTMG install on
  every launch, so they appear the moment you patch the game.
- **Packet ID changes after a Deca patch** — fetched live from the Crucible
  API on every launch; no restart needed.
- **New features from upstream RealmShark/Tomato** — a scheduled job merges
  them in every week, and a fresh build is published automatically.
- **New builds of Baghound itself** — Baghound checks for a newer release on
  every launch and installs it automatically before the main window opens.
  You'll briefly see an "Updating…" message during loading, then the app
  reopens on the new version with your settings and collection log carried
  over. If you stay running through a release, the status-bar button also
  flags a mid-session update you can install with one click.

You can also update by hand at any time — just re-download
`Baghound-windows.zip` from the
[latest release](https://github.com/Skydraex/ROTMG-packet-sniffer/releases/tag/latest)
and use that folder.

### Older versions & downgrading

Every published version is kept **permanently** on the
[Releases page](https://github.com/Skydraex/ROTMG-packet-sniffer/releases),
each under its own tag (`v2.0.0`, `v2.0.1`, …).

- The **`latest`** release always points at the newest build — this is what
  the Install section links to and what most people should use.
- Each **versioned** release (`v2.0.0`, `v2.0.1`, …) stays on the page
  permanently. Once a newer version supersedes it, it is left frozen — a
  stable point you can always come back to.

If a new build ever misbehaves, you can roll back: open the
[Releases page](https://github.com/Skydraex/ROTMG-packet-sniffer/releases),
pick an earlier `vX.Y.Z` release, and download its `Baghound-windows.zip`.
An older build keeps working indefinitely.

---

## Community & support

Questions, bug reports, feature requests, or just want to follow development?
[**Join the Baghound Discord**](https://discord.gg/BD8FFnhdve) — support
tickets, release announcements, and a place to share builds with other
players. For bugs you can also open an [issue on GitHub](https://github.com/Skydraex/Baghound/issues).

---

## Troubleshooting

| Problem | Fix |
|---|---|
| "Npcap not found" or no packets ever show up | Reinstall Npcap with the **WinPcap API-compatible mode** checkbox ticked. |
| Baghound opens but the DPS / Loot tabs stay empty | Click the **Start Sniffer** button (bottom-right), and make sure ROTMG is open. |
| Item names show as `???` or numbers | The asset extraction didn't find ROTMG. Confirm Exalt is installed via the official launcher. |
| Drops aren't posting to Discord | Open the **Discord** tab and check it shows "Connected". Remember only **tops** post (UT/ST, T7+ rings/abilities, T14+ armour/weapons, skins) — a brown/blue bag of filler won't. |
| The `.exe` won't launch after swapping in a new JAR | Don't hand-swap files — download a fresh `Baghound-windows.zip` and use that whole folder. |
| Multiple ROTMG clients open | Not supported by upstream RealmShark — only one client at a time. |
| Anything else | Open an [issue](https://github.com/Skydraex/ROTMG-packet-sniffer/issues) with what you tried, what happened, and the build id shown in the status bar. For a tracking bug (loot, collection, fame), also attach the debug logs from `%USERPROFILE%\.rotmg-sniffer\debug\`. **Grab them right after you stop the sniffer** — each new session (starting the sniffer again, or relaunching Baghound) wipes the logs fresh, so collecting them after a restart gives an empty file. |

---

## What this build adds

Upstream RealmShark/Tomato does all the core work — DPS tracking, loot
detection, chat, quests, asset extraction, packet parsing. Baghound keeps all
of it and adds the following.

**1. Stability & crash fixes.** The headline fix is a patch to the
upstream packet sniffer. Upstream has two compounding concurrency bugs:

1. **Lost-wakeup race** — the producer's `notifyAll()` can fire in the window
   between the consumer's drain and its next `wait()`, leaving the consumer
   blocked forever.
2. **Incorrect hand-rolled ring buffer** — wrap-around state desyncs, the
   resize path can leak the read pointer past unread data, and `isEmpty()`
   can return `true` while data sits in the buffer.

Either bug alone produces the "capture stops after ~30s" symptom; together
they make it virtually certain on long sessions. Both are replaced with a
`java.util.concurrent.LinkedBlockingQueue` and a `CountDownLatch`. The build
also hardens the packet pipeline against desync-driven crashes (guarded asset
loading, packet-constructor recovery, out-of-memory containment).

**2. Pixel-art UI redesign** — every screen rebuilt in Baghound's own retro
style, with five live-switchable themes (Dark, Light, Midnight, Ember, Purp)
and a drag-to-reorder tab bar.

**3. DPS logger — detailed combat log** — on top of upstream's per-player
damage tracking, Baghound records each player's damage taken, shows the HP%
players nexus at, keeps a persistent per-boss history of past runs, and
exports any leaderboard as text or an image card.

**4. Statistics tab** — a per-character fame-over-time graph with selectable
ranges, a per-day fame table, and a Dungeon Stats screen that ranks and
features your most-run dungeons with their boss sprites.

**5. Collection log** — a persistent, cross-session record of notable drops:
a lit/dim grid, a live "still-owned" view with automatic dismantle / death /
loss detection and vault-backed self-correction, a dated log, and shareable
text / image export.

**6. Loot drops to Discord** — the "tops" filter and the rendered loot card,
postable to any number of channels.

**7. RealmShark bot bridge** — guild loot bridging (the Bridge Review / Bridge
Logs tabs), ported from the PPETomato build.

**8. In-app updates** — silent auto-update on every launch, plus a no-pop-up,
status-bar self-update for mid-session releases.

**9. Automated builds & releases** — CI builds the Windows `.exe`, publishes a
rolling `latest` release plus a permanent per-version archive, and merges
upstream weekly.

---

## Credits & licensing

**Baghound is built and maintained by [Skydraex](https://github.com/Skydraex).**

The core sniffing engine — DPS tracking, loot detection, chat, quest UI, asset
extraction, packet parsing — is the work of the **RealmShark / Tomato** authors
at <https://github.com/X-com/RealmShark>. That engine is **MIT licensed** and
its original notice is reproduced in
[`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md), as that license requires.

The RealmShark bot bridge (the Bridge Review / Bridge Logs tabs) is ported from
the **PPETomato** build, a RealmShark variant that adds guild loot bridging.

Everything original to Baghound — the stability and crash-hardening patches,
the pixel-art interface and themes, the DPS logger, the Statistics tab, the
collection log, the Discord loot webhook, the in-app updater, the build / CI /
upstream-sync automation, and the [**baghound.app**](https://baghound.app)
companion website with its Cloudflare Workers backend — is © **Skydraex**, all
rights reserved. Baghound builds on RealmShark and Tomato, which are
MIT-licensed (see [`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md)) — that
licence is kept intact and the upstream attribution is preserved in full as
the MIT terms require.

**Baghound itself is proprietary.** The compiled application distributed from
this repository's Releases is licensed under the terms in [`LICENSE.md`](LICENSE.md):
personal use only, no redistribution, no reverse engineering, no derivative
works. The upstream RealmShark/Tomato engine remains MIT and you retain your
rights to that engine itself — but the combined Baghound build, including all
original additions, is not open source.
