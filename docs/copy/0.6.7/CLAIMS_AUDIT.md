# AION Sentinel 0.6.7 — Public copy and claims

Prepared **10 October 2026** for the current English release copy. This is a source and package review, not an application or live-game test result.

| Topic | Public facts and limits |
| --- | --- |
| Release | 0.6.7 Unfinished Beta; no new application, functional, unit, integration, executable, OCR, UI or live-game tests. Build and integrity checks are structural evidence only. |
| Platform | Targets Windows 10/11 x64 and the AION 2 EU / International English PC client; newly tested compatibility is not established. |
| Controls | Combat HUD, Start / Stop observation and Damage meter; beginner observation and capture controls are independent. Expert controls remain available. |
| Npcap setup | When absent, guided setup downloads the fixed official Npcap 1.89 installer after user consent and checks its pinned SHA-256 and publisher signature before opening the normal visible installer with Windows elevation. Existing installations skip setup. The installer is not bundled; license acceptance and options remain manual. |
| Cancellation and reboot | Cancellation, declined elevation and failure leave capture off. A required reboot does not restart Windows or enable the meter. Otherwise, component recheck precedes worker retry. |
| Inventory | 1,002 profiles: 223 with some warning support, 779 identity-only; partial rule support is separate from full mechanic and live-fight coverage. |
| World / high-GS scope | 54 world entries / 51 profiles, 83 source instance-map variants with explicit entrance GS ≥1,400; 137 combined target profiles, 72 with some warning support and 65 identity-only. GS is not read from the player. |
| Meter | Captured actor damage across targets, with evidence-dependent identities and run boundaries. Complete party coverage and automatic per-boss reset are not established. Current EU accuracy is unverified. |
| Package | 95,229,372 bytes (95.23 MB / 90.82 MiB), 428 extracted files; below 100,000,000 bytes. Internal signatures are separate from Windows Authenticode signing. |
| Creators | Neophrythe & Dr.Tatsu; GitHub maintainer neophrythe; bundled third-party notices and covered-source rights remain in the distribution. |
| Independence | No NCSOFT or Deadly Boss Mods affiliation, official approval or account-safety guarantee. |

Archive SHA-256: `5ca75e8ecebac0277c1f5b89bbb4af8a06a458913698952b06de95d8457e7fb0`. [0.6.7 release](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases/tag/v0.6.7) · [coverage](../../../guides/COVERAGE.md) · [meter guide](../../DAMAGE_METER.md).

Historical 0.6.6 artwork and motion remain illustrative, with simulated cues and damage. They do not establish 0.6.7 behavior or a measured boss timeline.
