# Sentinel 0.6.7 — guided Npcap setup, Unfinished Beta

Created by **Neophrythe & Dr.Tatsu**.

This preview adds guided setup for the optional live damage meter when Npcap is absent. No new application, executable, UI, OCR, functional, unit, integration or live-game tests were run. Compilation and file/archive integrity checks provide structural evidence only; earlier versions' results do not establish this version's behavior.

## Implemented changes

- Enabling **Damage meter** checks for the required installed capture components. An existing Npcap installation skips setup and proceeds to Sentinel's bundled capture worker.
- If Npcap is absent, Sentinel offers guided setup for the fixed **Npcap 1.89** installer from its official publisher. Download requires the user's consent. Sentinel checks the pinned SHA-256 and publisher signature before opening the installer. The driver and installer are not bundled in Sentinel's archive.
- Setup opens the normal visible Npcap installer with Windows elevation. The user reviews the publisher's license and chooses installation options. There is no silent installation or automatic license acceptance.
- Cancelling setup, declining elevation or an installation failure leaves the meter off while screen OCR remains available. A required reboot leaves capture off; Sentinel does not restart Windows. Without a reboot requirement, Sentinel rechecks the required capture components before retrying its worker.
- The beginner controls remain **Combat HUD**, **Start / Stop observation** and **Damage meter**. Observation and capture stop independently through those controls and F8. The legacy **Stop** button in Expert controls stops both.

Npcap remains a separate third-party prerequisite. Having its components installed does not guarantee capture permissions or successful decoding of the current game protocol. An administrator-only installation can require administrative capture rights. See [Damage meter](DAMAGE_METER.md) and [automatic quick start](BEGINNER_MODE.md).

## Unchanged coverage and limits

The catalog remains **1,002 profiles: 223 with some warning-rule support and 779 identity-only**. This release does not add mechanic coverage or establish that a listed skill cue appears in the current English game client. Identity coverage, warning-rule support and complete live-fight support remain separate claims.

The reviewed registry still identifies 54 public world-boss entries across 51 distinct profiles and 83 source instance-map variants with explicit entrance requirements of at least 1400 GS. Together they identify 137 profiles, of which 72 have some warning support and 65 remain identity-only. GS is a documented source entrance requirement, not a reading of the player's equipment.

Warnings require observed, matching English HUD evidence. Some source skill labels are configured hidden. Unknown timings, absent cues and ambiguous boss identities are not filled with guesses. Full phase bindings, warning lead times and complete encounter coverage remain unfinished. See [coverage and validation status](../guides/COVERAGE.md).

The meter retains its aggregate counter across captured actors and targets, with a shared elapsed interval. An ordinary boss death does not promise a separate counter for every fight. Names require separate identity records; keep capture enabled through a login or area change when names are pending. Current EU protocol coverage and combat accuracy remain unverified.

## Package and operation

Extract the complete **0.6.7 Unfinished Beta** archive into its own writable directory. Launch `Start-AION-Sentinel.cmd` or `AION-Sentinel.exe`; keep `_internal`, `meter`, models, data and notices together. Do not mix files from different versions. Capture is off at startup. Screen OCR and the simulated meter demo do not require Npcap; the guided installer download requires an internet connection.

The portable package compiles Sentinel's implementation to native code and retains the existing native meter worker, OCR models and third-party notices. Own-file integrity uses an internal RSA release manifest. This is not Windows Authenticode signing and cannot prevent all reverse engineering. Third-party covered-source access and Qt replacement rights remain available. See [native binary distribution](protected/BINARY_DISTRIBUTION.md).

The 7z archive is **95,230,316 bytes (95.23 MB / 90.82 MiB)** with **428 extracted files**, below **100,000,000 bytes**. SHA-256: `8bf3507d1a41e58e4323bd74187b0a9434ee6e504d176b0f0f6d6a0e97e5b9f1`. Download it from the [0.6.7 prerelease page](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases/tag/v0.6.7). Compression and integrity checks do not show that the UI starts, the installer succeeds, OCR recognizes a boss, live capture works or a warning fires in a fight. Those checks remain unperformed for this preview.
