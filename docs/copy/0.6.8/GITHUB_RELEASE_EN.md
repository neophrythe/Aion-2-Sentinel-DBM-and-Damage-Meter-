# AION Sentinel 0.6.8 — Unfinished Beta

Created by **Neophrythe & Dr.Tatsu**.

**Active development — gameplay validation pending.**

AION Sentinel is a desktop companion for the **AION 2 EU / International English PC client** on **Windows 10/11 x64**, with boss warnings, a movable combat HUD and an optional damage meter.

## What's new

- **Measured cast-end estimates.** A recognized owned skill beside explicit remaining seconds or a changing visible target-cast bar can supply a **cast (est.)** countdown and an estimated cast-ending heads-up. A skill name alone never starts a clock.
- **Inspect skill timing facts.** Expert Cues, the boss library and GameData show reviewed timing metadata for **550 accepted skill IDs across 209 profiles**, including raw cast/cooldown values, visibility flags and configured range-warning leads.
- **Adjust the heads-up.** Expert Cues adds **Cast-end heads-up (s)**, defaulting to 3 seconds and adjustable from 0 to 30 seconds. Automatic observation requires no new beginner control or calibration step.
- **Keep estimates tied to evidence.** Fresh, consistent independent measurements sustain a cast estimate. Frozen or missing measurements expire it; focus, target/profile changes, reset and stopping clear stale cast state. Journals and replay retain validated timing.

These estimates concern the observed cast's end. They do not provide individual wave impacts, jump moments or recurring fight schedules. Hidden, ambiguous or unsupported cast displays can leave the countdown absent. Raw cast/cooldown values do not establish seconds or repeat intervals.

## Install and use

1. Extract the **complete archive into its own writable folder**. Keep `_internal`, `meter`, models, data and notices together.
2. Launch **Start-AION-Sentinel.cmd** or **AION-Sentinel.exe**.
3. Keep the English game client in windowed or borderless mode with its target and minimap headings visible. Enable **Combat HUD**, choose **Start observation**, then bring the game to the foreground.
4. Enable **Damage meter** separately if wanted. Observation and capture stop independently through the beginner controls.

Automatic cast measurement belongs to foreground observation with automatic HUD discovery. Custom manual-region mode does not supply automatic target-cast timing. **F7:** Combat HUD · **F8:** Start / Stop observation · **F9:** Reset encounter.

The optional meter retains guided setup for **Npcap 1.89**. If Npcap is absent, setup downloads the fixed official installer only with your consent, checks its pinned SHA-256 and publisher signature, then opens the normal visible installer and Windows elevation prompt. You review the license and installation options yourself. Existing Npcap skips setup; the driver and installer are not bundled. Cancellation, declined elevation or failure leaves capture off while OCR remains available. A required reboot leaves capture off and does not restart Windows; otherwise Sentinel rechecks components before retrying its worker.

## Coverage and validation

The catalog remains **1,002 profiles: 223 with some warning-rule support and 779 identity-only**. The timing inventory describes source facts, not verified live visibility or complete encounter timelines. Some identified bosses still lack important mechanics. Current EU damage accuracy and gameplay behavior remain unverified.

**Unfinished Beta.** Gameplay validation is pending; compilation, signed-file integrity and archive roundtrips have been checked. These structural checks do not establish application behavior, cast-end accuracy or successful warnings in a fight. Earlier releases' results do not validate this version.

## Download

[Download 0.6.8 for Windows x64](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases/download/v0.6.8/AION-Sentinel-0.6.8-beta-windows-x64.7z) · [Release page](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases/tag/v0.6.8)

- Archive: `AION-Sentinel-0.6.8-beta-windows-x64.7z`
- Size: **95,352,628 bytes — 95.35 MB / 90.94 MiB**
- Extracted files: **430**
- Archive limit: **100,000,000 bytes**, with **4,647,372 bytes** remaining
- SHA-256: `14eec381b0baec79440c56560f904a4f03cd05af0af2a20241a1c0343bdc9287`

The package includes third-party notices and an internal signed-file manifest. That manifest is separate from Windows Authenticode publisher signing. Keep notices with the application.

[Project and documentation](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-) · [Report a problem](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/issues)

AION Sentinel is independent of NCSOFT and Deadly Boss Mods. Official approval and account-safety guarantees have not been established.
