# AION Sentinel 0.6.7 — Unfinished Beta

**Active development — gameplay validation pending.**

**Boss warnings and an optional damage meter in one compact desktop companion.**

AION Sentinel is a DBM-inspired companion for the **AION 2 EU / International English PC client**, targeting **Windows 10/11 x64**. Its beginner window has three controls: **Combat HUD**, **Start / Stop observation** and **Damage meter**.

**0.6.7 — Unfinished Beta.** Active development with partial boss-mechanic coverage. Gameplay validation is pending; compilation and package integrity have been checked.

## What's new

Application labels, release documents and presentation material now consistently use **Unfinished Beta**, with credits for **Neophrythe & Dr.Tatsu**.

Enabling the optional meter now offers guided setup when Npcap is absent. With your consent, Sentinel downloads the fixed **Npcap 1.89** installer from its official publisher, checks the pinned SHA-256 and publisher signature, and opens the visible installer with Windows elevation. You review the publisher's license and installation options yourself. There is no silent installation or automatic license acceptance, and the installer is not bundled in the archive.

An existing Npcap installation skips setup. Cancellation, declined elevation or installation failure leaves capture off while screen OCR remains available. If a reboot is required, Sentinel leaves the meter off and does not restart Windows. Otherwise, it rechecks capture components and retries its bundled worker. Capture permissions and current-game decoding can still prevent readings.

The automatic observation path and movable action warnings, Imminent bars and Upcoming bars remain available. Expert controls support custom HUD layouts. Timing estimates retain their `~` marker.

## Coverage

The catalog remains **1,002 profiles: 223 with some warning-rule support and 779 identity-only**. A supported rule is not complete phase, timing or live-fight coverage. Some source skill labels are hidden in game data and may never appear on screen. Unavailable cues and unknown timings remain unfilled.

The reviewed registry contains **54 known world-boss entries across 51 distinct profiles** and **83 source instance-map variants with explicit entrance requirements of at least 1400 GS**. Together they identify **137 profiles: 72 with some warning support and 65 identity-only**. These source lists do not guarantee current EU availability or complete mechanic support.

## Download

[Download the 0.6.7 Unfinished Beta for Windows x64 archive](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases/download/v0.6.7/AION-Sentinel-0.6.7-beta-windows-x64.7z)

- Archive: `AION-Sentinel-0.6.7-beta-windows-x64.7z`
- Size: **95,229,372 bytes — 95.23 MB / 90.82 MiB**
- Extracted files: **428**
- SHA-256: `5ca75e8ecebac0277c1f5b89bbb4af8a06a458913698952b06de95d8457e7fb0`

## Get started

1. Extract the complete archive into a writable folder and keep its files together.
2. Launch **Start-AION-Sentinel.cmd**.
3. Run the English game client in windowed or borderless mode with its target and minimap headings visible.
4. Enable **Combat HUD**, choose **Start observation**, then bring the game to the foreground.
5. Enable **Damage meter** if wanted. If Npcap is absent, accept guided setup and complete the visible installer. If setup requires a reboot, enable the meter again after restarting Windows. You can also install Npcap yourself from [the publisher's download page](https://npcap.com/#download).

**F7:** Combat HUD · **F8:** Start / Stop observation · **F9:** Reset encounter

Observation and capture have independent beginner controls. Stopping capture clears its table and hides the damage HUD; switching it off and on starts a fresh measurement.

## Damage meter and remaining gaps

The worker selects an adapter from decoded game evidence and displays captured damage, DPS and share. Names require separate identity records. If capture begins after login, keep it enabled through a login or area change; unknown identities retain numeric labels.

The default meter aggregates captured actors and targets. An ordinary boss death does not isolate or reset every fight. Missing metadata, permissions and protocol changes can limit readings. Current EU damage accuracy, full phase bindings, exact warning lead times and complete boss coverage remain unverified or unfinished.

The package includes application integrity checks, not Windows Authenticode signing or complete reverse-engineering protection. Screen OCR and the simulated meter demo work without Npcap.

Created by **Neophrythe & Dr.Tatsu**. [Project and source notices](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-) · [Report a problem](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/issues)

AION Sentinel is independent of NCSOFT and Deadly Boss Mods. Official approval and account-safety guarantees have not been established.
