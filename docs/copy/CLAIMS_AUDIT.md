# AION Sentinel 0.6.6 — Marketing claims audit

Prepared **10 October 2026**. Applies to the English copy in this folder and the associated 0.6.6 presentation. This is a source and package evidence review; no new application or live-game tests were performed.

## Evidence

- [0.6.6 package manifest](../../releases/v0.6.6/AION-Sentinel-0.6.6-beta-windows-x64.7z.manifest.json): size, hash, 428-file inventory, archive structure and lossless extraction checks.
- [0.6.6 validation record](../../releases/v0.6.6/AION-Sentinel-0.6.6-beta-windows-x64.7z.status.json): `structural_checks_only`, zero new functional/unit/integration/live tests, zero executable launches, no inherited test reports used.
- `aion_sentinel/ui.py` and `aion_sentinel/automatic_mode.py`: default three-control interface, automatic standard-HUD recognition, shared variant-text behavior and HP exclusions for unresolved modes.
- `aion_sentinel/assets/boss_warning_reference.json` and the additional reference helpers: source-backed warning inventory, not live cue validation.
- `aion_sentinel/assets/encounter_targets.json` and `docs/ENCOUNTER_TARGETS.md`: exact world-list joins, explicit GS requirements, source map variants and targeted coverage.
- `docs/DAMAGE_METER.md`, `aion_sentinel/damage_meter_panel.py`, `native/SentinelMeter/Worker/Program.cs`, automatic capture and combat-engine sources: optional bundled meter, adapter selection, prerequisites, identity-record dependence and cumulative counter behavior.

## Approved wording and limits

| Topic | Supported wording | Required qualification |
|---|---|---|
| Release state | “0.6.6 Unfinished Beta.” | Compilation and archive checks do not establish working live fights. No old test totals may be presented as current validation. |
| Client/platform | “For the AION 2 EU / International English PC client; targeting Windows 10/11 x64.” | Intended target, not newly tested compatibility. |
| Default controls | “Combat HUD, Start / Stop observation, Damage meter.” | Expert configuration remains available for nonstandard layouts. |
| Automatic recognition | “Finds standard visible name, level and location headings and selects compatible profiles when evidence is clear.” | Hidden/custom HUDs, unreadable text and ambiguous variants can prevent selection. |
| Unknown difficulty | “Shared NPC-owned English skill-text warnings can remain active.” | HP thresholds specific to a difficulty remain excluded; no inferred mode or phase. |
| Profile inventory | “1,002 profiles: 223 with some warning support, 779 identity-only.” | These are profiles and partial rule coverage, not 1,002 solved or live-tested bosses. |
| World inventory | “54 known source world-boss entries across 51 distinct profiles.” | Duplicate names exist. Identity completeness is bounded to the reviewed list. |
| High-GS inventory | “83 source instance map variants with explicit entrance requirements >= 1400 GS.” | Map variants are not 83 distinct dungeons; availability and live implementation are not guaranteed. |
| Targeted coverage | “137 targeted profiles: 72 with some warning support, 65 identity-only.” | A warning-supported profile can still lack most encounter mechanics. |
| Skill warnings | “Warnings from observed matching English text.” | Static labels may be hidden and never visible. No universal screen-detection claim. |
| Timer bars | “Estimates marked ~ where timers are available.” | No exact timing or complete mechanic-order promise. |
| Meter integration | “Optional bundled passive worker with automatic adapter discovery.” | Separately installed Npcap and capture permissions remain required. |
| Player names | “Shows names when identity records are received.” | Late activation, missing records or protocol changes can leave numeric labels. |
| Party damage | “Shows captured actor damage.” | Complete teammate coverage, authoritative party membership and summon attribution are not guaranteed. |
| DPS interval | “Aggregate counter across captured actors and targets.” | An ordinary boss death does not automatically isolate or reset each fight. |
| Protected package | “Native compilation and signed internal file manifests.” | Not Authenticode signing or complete reverse-engineering prevention. |
| Package | “95,189,963 bytes, 428 files, lossless 7z compression.” | 95.17 decimal MB / 90.76 binary MiB; under 100,000,000 bytes. Integrity is not malware or gameplay certification. |
| Maintainer | “Maintained by neophrythe.” | Third-party licenses and source notices remain in the distribution. No unsupported artwork-authorship claim. |
| Independence | “Independent of NCSOFT and Deadly Boss Mods.” | No official approval, legality certification or account-safety guarantee. |

Archive SHA-256: `948ade7b35e2d8b40f430150680ee337068262f1be63ab61eb6c0d99ebe11ba2`.

## Claims to exclude

- “Every boss ready”, “all phases complete”, “100% accurate”, “perfect timings” or “fully live-tested”.
- “54 distinct world bosses” or “83 complete dungeons”; the inventory is 54 entries / 51 profiles and 83 map variants.
- “No dependencies”, “names always known”, “complete party DPS” or “automatic per-boss DPS reset”.
- “Official”, “NCSOFT approved”, “legal-certified”, “ban-safe”, “undetectable” or “anti-cheat safe”.
- “Impossible to reverse engineer”, “Windows signed” or unqualified security guarantees.
- Historical test counts reused as 0.6.6 validation or simulated images presented as current live-game captures.

Keep preview illustrations and motion demonstrations labeled as simulated. Preserve readable limits near the download and feature copy, including the Unfinished Beta status and Npcap prerequisite.
