# AION Sentinel 0.6.7 — FAQ

## What does Sentinel do?

Sentinel displays DBM-inspired boss warnings in a separate desktop overlay and includes an optional damage meter. Its intended client is AION 2 EU / International in English, on Windows x64.

## Is this release fully tested?

0.6.7 is Unfinished Beta, in active development with partial boss-mechanic coverage. Gameplay validation is pending; compilation and package integrity have been checked. Older releases' results do not establish current-game behavior.

## Do I need to select profiles and draw OCR boxes?

The default interface automatically looks for standard target names, levels and minimap location headings, then selects a compatible profile when the evidence is clear. You start with **Combat HUD**, **Start / Stop observation** and **Damage meter**. Hidden headings and custom layouts can still require expert configuration.

## What happens if the difficulty is unknown?

When compatible variants have verified shared English skill names, Sentinel can use their common text cues. It does not guess difficulty-specific HP thresholds. Without a usable shared cue or clear identity, a catalog match alone cannot produce a mechanic warning.

## Does it support every boss?

The catalog contains **1,002 profiles: 223 with some warning support and 779 identity-only**. A profile with some support can still lack most phases and timings. Full live-game coverage is not established.

The reviewed world list includes **54 entries / 51 distinct profiles**, covering Verteron, Altgard and Abyss. The targeted registry also includes **83 source instance map variants with explicit entrance requirements of at least 1400 GS**. Those world and high-GS lists identify **137 profiles: 72 with some warning support, 65 identity-only**. These source-bounded counts do not prove current EU availability or accurate recognition of every encounter.

## Why might a known skill produce no warning?

The screen observer must see readable English text matching the cue. Some English labels exist only in game data and are configured as hidden. Identity metadata, a skill name or a static HP reference is not proof of a visible, correctly timed cue.

## Are the timers exact?

No. Exact schedules and warning lead times are incomplete. Available timing estimates retain the `~` marker. Sentinel does not infer precise countdowns from an attack name.

## Does the meter need a separate application?

No. Its native worker ships in Sentinel's portable folder and starts from **Damage meter**. It discovers active network adapters automatically and selects a connection from decoded game evidence.

## Does the meter need a driver?

Live capture requires a separate [Npcap installation](https://npcap.com/#download) and permission to open its capture adapters. If Npcap is absent, Sentinel offers guided download of the fixed official Npcap 1.89 installer after your consent, checks its pinned SHA-256 and publisher signature, and opens its visible installer with Windows elevation. You review the license and select options yourself; the installer is not bundled and installation is not silent. An existing installation skips setup.

Cancellation, declined elevation or failure leaves the meter off while OCR remains available. A required reboot leaves capture off without restarting Windows automatically. Otherwise, component recheck precedes worker retry. Resolve any reported capture permission issue and enable the meter again.

## Will teammates appear with their names and damage?

Captured damage is grouped by observed actor ID. Names appear when the required identity records are received; missing records leave numeric labels. If you enabled capture after login, keep it enabled through a login or area change. Party membership, summon attribution and complete teammate damage coverage can remain incomplete.

## Does DPS reset after every boss?

The default meter aggregates captured actors and targets over the current run. An ordinary boss death does not reset it or isolate every fight. The backend has evidence-dependent run boundaries, including changed dungeon/zone labels and confirmed catalogued final-boss completion. Switch the meter off and on to explicitly start a fresh counter. Missing metadata or protocol changes can affect those boundaries.

## Can I move the warnings?

The action-warning, Upcoming and Imminent surfaces have separate movable positions. The damage HUD is a separate overlay. Expert settings expose positioning and lock controls.

## Is this an official or account-safe game add-on?

Sentinel is independent of NCSOFT and Deadly Boss Mods. Official approval and account-safety guarantees have not been established. This project makes no anti-cheat compatibility guarantee.

## Is the executable protected?

The package uses native compilation and signed internal file manifests. That does not prevent every form of reverse engineering, and it is not Windows Authenticode signing. The archive retains the required third-party notices and source-availability information.

## Where do I download it or report problems?

Created by **Neophrythe & Dr.Tatsu**. [Download 0.6.7](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases/download/v0.6.7/AION-Sentinel-0.6.7-beta-windows-x64.7z), visit the [project](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-) or open an [issue](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/issues). The archive is **95,229,372 bytes**, with **428 extracted files**. Keep the complete folder together.
