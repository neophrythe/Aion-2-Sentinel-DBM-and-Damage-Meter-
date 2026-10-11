# AION Sentinel — Boss Warnings + Damage Meter

Created by **Neophrythe & Dr.Tatsu**.

**0.6.10 — Unfinished Beta. Active development — gameplay validation pending.**

AION Sentinel brings DBM-inspired boss warnings and an optional damage meter to the **AION 2 EU / International English PC client**. It runs alongside the game as a separate **Windows 10/11 x64** desktop companion with a movable combat HUD.

## New in 0.6.10

This release combines the 0.6.9 encounter and meter improvements with compact, sourced combat research. It retains the three beginner controls: **Combat HUD**, **Start / Stop observation** and **Damage meter**.

- **88 published mechanic references from 16 sources**, associated with **42 catalog profiles** where identity and instance match. The expert encounter guide shows reactions, approximate HP ranges, timing types, source links and source limitations. Shortened guide titles are reference associations; they do not become OCR aliases.
- **48 typed timing fields** distinguish cast duration, effect lifetime, windup, telegraph lead and hit spacing. These are publisher claims, with their original quality and difficulty context. They never supply automatic recurrence, phase transitions or player-relative jump clocks.
- Exact owned English skill rules can display associated research notes. Existing curated responses take precedence. A compatible additional explicit-label response upgrades unchanged generated wording; custom messages and disabled rules remain respected.
- Aggregate public EU log identity evidence is visible for **137 targeted profiles**. Logs can identify a boss variant without supplying a mechanic timeline. No player logs, account data, GPL implementation or original bot binaries are included.
- Automatic profile synchronization is now retained in recording, replay and descriptive timing analysis. Cast-observation state is reset when synchronized settings change.



## Three controls to begin

- **Combat HUD:** show or hide the boss-warning overlay.
- **Start / Stop observation:** follow visible English target and location text automatically.
- **Damage meter:** start or stop the bundled passive capture worker and its separate damage HUD.

Compatible encounter profiles and standard HUD regions are selected automatically. Normal enemies stay quiet. Observation and capture stop independently through the beginner controls and F8. Optional expert tools remain available for custom HUD layouts; manual-region mode does not supply automatic target-cast timing.

Movable action warnings, Imminent and Upcoming bars, local OCR models and an available English Windows speech voice remain included. Timer estimates retain their **~** marker.

## Guided setup for the optional meter

If Npcap is already installed, Sentinel skips setup. Otherwise, enabling **Damage meter** offers **Set up Npcap**. With your consent, Sentinel downloads the fixed **Npcap 1.89** installer from its official publisher, checks the pinned SHA-256 and publisher signature, then opens the normal visible installer and Windows elevation prompt. Review the publisher's license and choose installation options yourself.

The installer and driver are not bundled. There is no silent installation or automatic license acceptance. Cancellation, declined elevation or failure leaves capture off while screen OCR remains available. A required reboot leaves the meter off and does not restart Windows; restart when convenient, then enable the meter again. Otherwise Sentinel rechecks capture components before retrying its worker. Capture permissions can still prevent readings. Manual installation from [the publisher's download page](https://npcap.com/#download) is also available.

The meter displays captured damage, DPS and share. Names arrive separately; keep capture running through login or an area change if names are pending. Its default measurement aggregates captured actors and targets and may include non-party actors. Captured targets and confirmed party members can be filtered in Expert controls. Local history keeps up to 100 reports within 32 MiB; attempt and run reports overlap. Current EU damage accuracy remains unverified.

## Coverage and development status

The catalog contains **1,002 profile identities**; mechanic coverage remains partial. The reviewed world/high-GS subset has **137 profiles**. Research identity counts do not establish cast or phase coverage. These counts and the 550/209 timing inventory describe source coverage, not complete phases, every boss mechanic or verified live recognition.

**Unfinished Beta.** Gameplay validation is pending; compilation and package integrity have been checked. These checks do not establish in-game warning behavior or cast-end accuracy. Full wave sequences and recurring encounter schedules remain unfinished.

## Install and use

Extract the complete archive into its own writable folder and launch **Start-AION-Sentinel.cmd**. Keep all runtime folders, models and notices together. Run the English game in windowed or borderless mode, keep target/minimap headings visible, enable **Combat HUD**, choose **Start observation** and bring the game to the foreground. Enable the meter separately if wanted.

**F7:** Combat HUD · **F8:** Start / Stop observation · **F9:** Reset encounter

Archive: `AION-Sentinel-0.6.10-beta-windows-x64.7z` · **95,292,144 bytes** (95.29 MB / 90.88 MiB), 433 files. Strict limit: 100,000,000 bytes.

SHA-256: `8aa341143ef8ce79a0d585ca4acc409b6992c9c083f33b46de4db1fad1cc0743`

## Downloads and support

[0.6.10 release and documentation](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases/tag/v0.6.10) · [Project](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-) · [Issues](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/issues)

The package's internal integrity signatures are separate from Windows Authenticode signing. AION Sentinel is independent of NCSOFT and Deadly Boss Mods; official approval and account-safety guarantees have not been established.
