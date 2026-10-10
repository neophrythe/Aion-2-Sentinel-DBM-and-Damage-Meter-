# AION Sentinel — Boss Warnings + Damage Meter

**Active development — gameplay validation pending.**

AION Sentinel brings DBM-inspired warnings and an optional damage meter to the **AION 2 EU / International English PC client**. It runs as a separate Windows desktop companion with a movable combat HUD.

**0.6.7 — Unfinished Beta.** Active development with partial boss-mechanic coverage. Gameplay validation is pending; compilation and package integrity have been checked.

## Three controls to begin

- **Combat HUD:** show or hide the boss-warning overlay.
- **Start / Stop observation:** read visible English game text and follow the target and location automatically.
- **Damage meter:** enable or stop the bundled passive capture worker, with guided Npcap setup if its prerequisite is absent.

Standard target names, levels and minimap headings are found automatically. Compatible profiles are selected from visible evidence. Unresolved difficulty can use shared, NPC-owned skill-text warnings while difficulty-specific HP hints stay unavailable. Expert controls remain available for custom HUD layouts. Observation and capture stop independently through the beginner controls and F8.

## Guided setup for the optional meter

Enable **Damage meter** when you want live readings. If Npcap is already installed, Sentinel skips setup. Otherwise, with your consent, it downloads the fixed **Npcap 1.89** installer from the official publisher, checks the pinned SHA-256 and publisher signature, and opens its visible installer with the normal Windows elevation prompt. You review and accept the publisher's license and choose installation options yourself.

The installer is not bundled. There is no silent installation or automatic license acceptance. Cancelling, declining elevation or installation failure leaves capture off; screen OCR remains available. A required reboot leaves the meter off and does not restart Windows automatically. Otherwise, Sentinel rechecks capture components and retries its worker. Administrator-only Npcap installations can still require administrative capture rights. Manual installation from [the publisher's download page](https://npcap.com/#download) is also available.

## Included and current coverage

- Separate movable action warnings, Imminent bars and Upcoming bars.
- English warning calls through an available Windows speech voice.
- Bundled local OCR models for screen observation.
- Captured player names, DPS, damage and share, with a separate damage HUD.
- Automatic adapter discovery without a separate meter application.
- A catalog of **1,002 profiles: 223 with some warning support and 779 identity-only**.

The reviewed registry contains **54 known world-boss entries / 51 distinct profiles** and **83 source instance-map variants with explicit entrance requirements of at least 1400 GS**. Together these identify **137 profiles: 72 with some warning support and 65 identity-only**. A rule or identity entry does not mean every mechanic or phase is implemented, visible or verified in the current client.

Warnings require readable, matching English text. Some source skill labels are hidden, and exact mechanic timings remain incomplete. Timer estimates retain their `~` marker.

## Install and use

Extract the complete portable archive into a writable folder and launch **Start-AION-Sentinel.cmd**. Keep the English game client in windowed or borderless mode with target and minimap headings visible. Enable **Combat HUD**, click **Start observation**, and return the game to the foreground. Enable the meter separately if wanted.

Names may remain numeric when capture starts after login. Keep capture running through a login or area change to receive fresh identity records. The default counter aggregates captured actors and targets; ordinary boss deaths do not automatically isolate every fight. Current EU protocol coverage and damage accuracy remain unverified.

**F7:** Combat HUD · **F8:** Start / Stop observation · **F9:** Reset encounter

Target platform: **Windows 10/11 x64**. The 7z archive is **95,229,372 bytes (95.23 MB / 90.82 MiB)** and contains **428 files**. Extract the complete archive.

## Download and support

[Downloads and release notes](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases) · [Project](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-) · [Issues](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/issues)

Archive: `AION-Sentinel-0.6.7-beta-windows-x64.7z` · SHA-256: `5ca75e8ecebac0277c1f5b89bbb4af8a06a458913698952b06de95d8457e7fb0`

Created by **Neophrythe & Dr.Tatsu**. This is an independent project with no NCSOFT or Deadly Boss Mods affiliation. Official approval and account-safety guarantees have not been established.
