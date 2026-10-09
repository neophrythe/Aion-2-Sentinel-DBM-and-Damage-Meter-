# AION Sentinel — Boss Warnings + Damage Meter

**Read the fight. Keep the information where you want it.**

AION Sentinel brings DBM-inspired warnings and an optional damage meter to the **AION 2 EU / International English PC client**. It runs as a separate Windows desktop companion with a movable combat HUD.

**Version 0.6.6 is an untested preview.** The package was built and checked for structural integrity; this version has not undergone new application or live-game testing.

## Three controls to begin

- **Combat HUD:** show or hide the boss-warning overlay.
- **Start / Stop observation:** read visible English game text and follow the target and location automatically.
- **Damage meter:** enable or stop the bundled passive damage-capture worker.

Standard target names, levels and minimap headings are found automatically. Compatible profiles are selected from the visible evidence. If difficulty is unclear, Sentinel can use shared skill-text warnings that belong to the candidate bosses; it does not select a difficulty-specific HP threshold by guesswork. Expert configuration remains available for custom HUD layouts.

## Included

- Separate movable action warnings, Imminent bars and Upcoming bars.
- English warning calls through an available Windows speech voice.
- Bundled local OCR models for the screen-observation path.
- An optional meter showing captured player names, DPS, damage and share, with a separate damage HUD.
- Automatic adapter discovery for the meter, without a separate meter application.
- A catalog of **1,002 profiles**, with warning and identity coverage clearly distinguished.

## What the catalog covers

**223 profiles have some warning support; 779 are identity-only.** Having a rule does not mean every mechanic or phase is implemented, or that its cue is visible and verified in the current game client.

The reviewed target registry contains **54 known world-boss entries / 51 distinct profiles** and **83 instance map variants with explicit entrance requirements of at least 1400 GS**. The combined registry identifies **137 profiles**, of which **72 have some warning support and 65 remain identity-only**. It is not a complete live-game compatibility claim.

Warnings require readable matching text. Some names come from hidden skill labels, and exact mechanic timings are incomplete. Where timer estimates are used, they remain marked `~`.

## Install and use

Extract the complete portable folder and launch **Start-AION-Sentinel.cmd**. Keep the English game client in windowed or borderless mode with its target and minimap headings visible. Enable **Combat HUD**, click **Start observation**, and return the game to the foreground.

The meter requires the separately installed [Npcap driver](https://npcap.com/#download). Screen OCR works without it. Names can be unavailable when capture starts after login; keep the meter running during a login or area change to receive fresh identity records. The default counter aggregates captured targets and actors, rather than automatically isolating every boss fight.

**F7:** Combat HUD · **F8:** Start / Stop observation · **F9:** Reset encounter

Target platform: **Windows 10/11 x64**. The preview has not been newly tested on either platform. The 7z download is **95.19 MB** and contains **428 files**; extract the whole archive.

## Download and support

[Download 0.6.6 — Untested Preview](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases/download/v0.6.6/AION-Sentinel-0.6.6-untested-windows-x64.7z) · [Project](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-) · [Issues](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/issues)

Maintained by **neophrythe**. This is an independent project with no NCSOFT or Deadly Boss Mods affiliation. Official approval and account-safety guarantees have not been established.
