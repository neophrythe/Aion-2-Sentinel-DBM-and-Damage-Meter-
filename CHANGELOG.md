# Release history

## 0.6.13 — 11 October 2026 — Unfinished Beta

DPS now uses a shared first-to-last hit interval with a one-second minimum. Recognised unresolved summon damage is retained and can be merged later with generation-scoped ownership. Compact damage ticks, bounded nested packets and NPC self-heal filtering are improved. Boss-only and all-target scopes are labelled clearly. Deus recognition, capture continuity, automatic boss attempts and bounded history improvements are included. 182 Python checks and 88 native worker assertions passed on this build. Complete frozen-application gameplay and the reported live DPS difference still require a matching encounter comparison.

Created by **Neophrythe & Dr.Tatsu**. [Release notes](releases/v0.6.13/README.md).

## 0.6.10 — 11 October 2026 — Unfinished Beta

0.6.10: 88 mechanic references from 16 sources, 48 typed timing fields, 42 profile associations, aggregate identity evidence for 137 targeted profiles, and profile synchronization retained in replay. Includes 0.6.9 channel-specific warnings, safer ownership, meter filters, independent damage HUD controls and bounded history. Complete phase schedules remain unavailable. Unfinished Beta.

Created by **Neophrythe & Dr.Tatsu**. [Release notes](releases/v0.6.10/README.md).

## 0.6.8 — 10 October 2026 — Unfinished Beta

Created by **Neophrythe & Dr.Tatsu**.

- Measured cast-end estimates from explicit visible remaining seconds or changing target-cast progress, with fresh independent evidence and stale-state clearing.
- Timing reference for 550 accepted skill IDs across 209 profiles, inspectable in Expert Cues, the boss library and GameData.
- An expert cast-end heads-up setting, default 3 seconds and adjustable 0–30 seconds; no new beginner controls.
- Validated timing retained in journals and replay, with measured timing accepted in identified structured cast observations.
- Portable archive: 95,352,628 bytes (95.35 MB / 90.94 MiB), 430 extracted files, below 100,000,000 bytes.

Gameplay validation is pending; compilation and package integrity have been checked. Raw casting/cooldown values do not become clocks, individual wave impacts or recurring fight schedules. Boss-mechanic coverage remains partial: 1,002 profiles, 223 with some warning support and 779 identity-only. See [0.6.8 release notes](releases/v0.6.8/README.md).

## 0.6.7 — 10 October 2026 — Unfinished Beta

Created by **Neophrythe & Dr.Tatsu**.

- Guided Npcap setup when the optional damage meter's capture components are absent; existing installations skip setup.
- User-consented download of the fixed official Npcap 1.89 installer, pinned SHA-256 and publisher-signature checks, then the normal visible installer and Windows elevation prompt.
- Manual publisher-license acceptance and installation options; no bundled capture driver or silent installation.
- Cancellation, declined elevation and failure leave capture off. A required reboot does not restart Windows or enable the meter automatically. Otherwise, component recheck precedes worker retry.
- The beginner observation and meter controls remain independent. Catalog coverage is unchanged: 1,002 profiles, 223 with some warning support and 779 identity-only.
- Portable archive: 95,229,372 bytes (95.23 MB / 90.82 MiB), 428 extracted files.

No new application, functional, unit, integration, executable, OCR, UI or live-game tests were run. Structural build and archive checks do not validate the setup flow or live fights. See [0.6.7 release notes](releases/v0.6.7/README.md).

## 0.6.6 — 10 October 2026 — Unfinished Beta

- A default beginner view with Combat HUD, observation Start/Stop and Damage meter.
- Automatic names, level/location discovery, compatible profiles and standard HUD search regions.
- Shared owned skill cues when Explore/Conquest remains unknown, with variant HP hints and timers withheld.
- A reviewed world-boss category and source GS ≥1,400 instance filters in the optional expert library.
- Published response advice linked to owned English skill labels, inspectable source references and explicit coverage gaps.
- An additional exact-owner/map-guarded Tetrata 50%-HP reinforcement reference.
- Independent observation and damage-capture controls, retained movable HUD layouts and F7/F8/F9 shortcuts.
- A native portable package under the strict decimal 100 MB limit, with unchanged OCR models and signed critical-file integrity.

No new behavior or live-fight tests were run. Complete mechanic coverage is still unavailable for some identified bosses.
