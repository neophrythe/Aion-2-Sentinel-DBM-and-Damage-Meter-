# Sentinel 0.6.8 — measured cast estimates, Unfinished Beta

Created by **Neophrythe & Dr.Tatsu**.

This release integrates the reviewed skill timing reference with passive target-cast measurements. Recognized explicit remaining seconds or a changing visible cast bar can now supply an estimated cast-end countdown and heads-up. Full wave sequences, recurring fight schedules and player-relative jump moments remain unfinished.

No new application, executable, UI, OCR, functional, unit, integration or live-game tests were run. Source syntax, compilation, signature and archive checks provide structural evidence only. Earlier releases' results do not establish 0.6.8 behavior.

## Implemented changes

- The packaged source reference includes **550 accepted skill IDs across 209 profiles**, with pinned English Steam data hashes, exact NPC skill ownership, raw cast/cooldown fields, range-warning leads and configured visibility. Expert Cues and local GameData views expose those facts.
- Automatic screen timing uses the small cue region under the confirmed target header, matches one exact owned English skill and requires fresh independent evidence. Explicit labels such as `3.2 s` can supply a remaining time; an optional conservative visible-bar check supplies progress.
- The encounter engine checks decreasing seconds or learns a duration from several changing bar measurements. It can follow an already running cast and never starts a clock from the first skill-name appearance. OCR-cache reuse and frozen measurements do not refresh it.
- The combat HUD shows cast-end estimates and an estimated cast-ending heads-up. Expert Cues keeps the heads-up threshold separate from user-measured repeat timers. No new calibration step or beginner control is required.
- Journals and replay retain validated screen timing. Structured observations can carry a measured cast remainder or progress together with a verified casting skill ID.
- Boss/profile/window changes, focus loss, reset and stopping clear stale cast state. Missing fresh timing expires the estimate.

## Source facts and remaining limits

Raw `CastingTime` and `NeedCoolTime` have no proved unit in the supplied data/export mapping. They remain raw values and supply no encounter clock or repeat schedule. Bakarma's `Wave of Death` retains `CastingTime=18000`, `NeedCoolTime=1000` and a reviewed **5000 ms / 5-second configured range-warning lead**. The latter is a static hint, not a synchronized future wave impact. See [cast timing](CAST_TIMING.md).

Configured gauge/text hiding can prevent a measurement, and the conservative bar check does not cover every HUD appearance. Missing, ambiguous or frozen cast evidence leaves the countdown absent. The 550/209 inventory describes reference facts rather than live-verified cast visibility or complete boss coverage. Gameplay validation remains pending.

The broader catalog remains **1,002 profiles: 223 with some warning-rule support and 779 identity-only**. Some supported profiles still lack important mechanics. Existing source HP hints, guide responses and user choices remain available. The native damage meter and guided Npcap setup retain their existing measurement limits; damage-hit skill IDs do not supply pre-impact cast events.

## Package and operation

Extract the complete **0.6.8 Unfinished Beta** archive into its own writable directory. Launch `Start-AION-Sentinel.cmd` or `AION-Sentinel.exe`; keep `_internal`, `meter`, models, data and notices together. Use the normal beginner **Combat HUD**, **Start / Stop observation** and **Damage meter** controls. Capture is off at startup. Automatic cast measurement belongs to foreground screen observation; custom manual-region mode supplies no automatic target-cast timing.

The archive is `AION-Sentinel-0.6.8-beta-windows-x64.7z`: **95,352,628 bytes (95.35 MB / 90.94 MiB)**, **430 extracted files**, below the **100,000,000-byte** limit. SHA-256: `14eec381b0baec79440c56560f904a4f03cd05af0af2a20241a1c0343bdc9287`. [Canonical archive metadata](../releases/v0.6.8/AION-Sentinel-0.6.8-beta-windows-x64.7z.manifest.json) records its file inventory and structural evidence. The package includes `CAST_TIMING.md`, `BETA_RELEASE.json` and `RELEASE_VALIDATION.md`. Compilation, own-file signatures and archive roundtrips do not prove that the application starts or a warning works in a fight. The release status remains **Unfinished Beta**.

The portable package compiles Sentinel's implementation to native code, retains OCR models and the native meter, and includes third-party notices and covered-source access. The internal RSA release manifest is not Windows Authenticode signing. See [native binary distribution](protected/BINARY_DISTRIBUTION.md), [user guide](USER_GUIDE.md) and [warning evidence](BOSS_WARNINGS.md).
