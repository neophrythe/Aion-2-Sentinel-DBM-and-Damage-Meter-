# AION Sentinel 0.6.6 — Unfinished Beta

**Boss warnings and a damage meter, in one compact desktop overlay.**

AION Sentinel is a DBM-inspired companion for the **AION 2 EU / International English PC client**, targeting **Windows 10/11 x64**. This preview simplifies the default window to three controls: **Combat HUD**, **Start / Stop observation** and **Damage meter**.

**0.6.6 is an Unfinished Beta.** The build and archive received structural and integrity checks. No new application, functional, unit, integration or live-game tests were run. Earlier versions' test results are not evidence that this build works in a live fight.

## What's new

- Automatic discovery of standard target-name, level and location headings, with compatible profile selection when the evidence is clear.
- A beginner interface that starts observation without choosing a profile or drawing capture regions. Expert settings remain available for custom layouts.
- Shared, NPC-owned English skill-text warnings when matching difficulty variants remain unresolved. Mode-specific HP hints stay disabled in this state.
- An expanded world-boss and high-GS encounter identity registry, with source-backed warning coverage kept separate from identity coverage.
- An integrated optional DPS meter with automatic network-adapter discovery. No separate meter application is needed.

Action warnings, Imminent bars and Upcoming bars have separate movable HUD positions. Available English Windows voices can speak warning calls. Timing estimates retain their `~` marker; a catalog entry does not supply an exact mechanic schedule.

## Coverage, without counting identities as completed fights

The catalog contains **1,002 profiles**. **223 have some warning-rule support; 779 remain identity-only.** A supported profile can have only an observed skill-text cue or a reference hint; this is not full phase, timing or live-fight coverage.

The targeted registry includes **54 known world-boss entries across 51 distinct profiles**, plus **83 source map variants with explicit instance entrance requirements of at least 1400 GS**. Together these identify **137 profiles: 72 with some warning support and 65 identity-only**. These are reviewed source lists, not a guarantee that every current EU boss or listed map is available or fully supported.

Warnings depend on readable, matching English HUD text. Some source skill labels are configured as hidden in game data and may never appear on screen. Unavailable cues and unknown timings are not filled with guesses.

## Download

[Download the 0.6.6 Unfinished Beta Windows x64 archive](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases/download/v0.6.6/AION-Sentinel-0.6.6-beta-windows-x64.7z)

- Archive: `AION-Sentinel-0.6.6-beta-windows-x64.7z`
- Size: **95,189,963 bytes — 95.19 MB / 90.78 MiB**
- Extracted files: **428**
- SHA-256: `948ade7b35e2d8b40f430150680ee337068262f1be63ab61eb6c0d99ebe11ba2`

## Get started

1. Extract the complete archive into a writable folder; keep the portable files together.
2. Launch **Start-AION-Sentinel.cmd**.
3. Run the English game client in windowed or borderless mode and make its target and minimap headings visible.
4. Enable **Combat HUD**, choose **Start observation**, then bring the game to the foreground.
5. Enable **Damage meter** if wanted. Live capture requires the separately installed [Npcap driver](https://npcap.com/#download); some installations also require administrative capture rights.

**F7:** Combat HUD · **F8:** Start / Stop observation · **F9:** Reset encounter

## Damage meter and remaining gaps

The worker chooses an adapter from decoded game evidence and displays captured player damage, DPS and share. Names require separate identity records: if capture begins after login, keep it enabled through a login or area change. Unknown names retain numeric labels rather than receiving guessed identities.

The default meter is an aggregate counter across captured actors and targets. An ordinary boss death does not isolate or reset every fight. Switching it off and on begins a fresh measurement. Protocol changes, missing metadata and capture permissions can prevent or limit readings; current EU damage accuracy has not been validated for this preview.

Full phase bindings, precise warning lead times and complete boss coverage remain unfinished. Custom or hidden HUD layouts can require expert configuration. The release includes application integrity checks, not Windows Authenticode signing or complete reverse-engineering protection.

Maintained by **neophrythe**. [Project and source notices](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-) · [Report a problem](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/issues)

AION Sentinel is independent of NCSOFT and Deadly Boss Mods. Official approval and account-safety guarantees have not been established.
