# AION Sentinel — Boss Warnings + Damage Meter

Created by **Neophrythe & Dr.Tatsu**.

**0.6.8 — Unfinished Beta. Active development — gameplay validation pending.**

AION Sentinel brings DBM-inspired boss warnings and an optional damage meter to the **AION 2 EU / International English PC client**. It runs alongside the game as a separate **Windows 10/11 x64** desktop companion with a movable combat HUD.

## New in 0.6.8

Recognized explicit remaining seconds or a changing visible target-cast bar can now supply a **cast (est.)** countdown and an estimated cast-ending heads-up. Sentinel checks fresh, consistent independent measurements; the first appearance of a skill name does not start a clock. Missing, ambiguous or frozen cast evidence leaves the countdown absent or lets it expire.

Expert Cues, the boss library and GameData expose reviewed timing facts for **550 accepted skill IDs across 209 profiles**. Expert **Cast-end heads-up (s)** defaults to 3 seconds and is adjustable from 0 to 30 seconds. The beginner controls need no extra switch or calibration step.

A cast-end estimate does not time individual waves, jump moments or repeating fight sequences. Raw casting and cooldown values remain reference data; they do not become seconds or repeat intervals. Some source skills hide their text or cast gauge, and supported cast displays remain limited.

## Three controls to begin

- **Combat HUD:** show or hide the boss-warning overlay.
- **Start / Stop observation:** follow visible English target and location text automatically.
- **Damage meter:** start or stop the bundled passive capture worker and its separate damage HUD.

Compatible encounter profiles and standard HUD regions are selected automatically. Normal enemies stay quiet. Observation and capture stop independently through the beginner controls and F8. Optional expert tools remain available for custom HUD layouts; manual-region mode does not supply automatic target-cast timing.

Movable action warnings, Imminent and Upcoming bars, local OCR models and an available English Windows speech voice remain included. Timer estimates retain their **~** marker.

## Guided setup for the optional meter

If Npcap is already installed, Sentinel skips setup. Otherwise, enabling **Damage meter** offers **Set up Npcap**. With your consent, Sentinel downloads the fixed **Npcap 1.89** installer from its official publisher, checks the pinned SHA-256 and publisher signature, then opens the normal visible installer and Windows elevation prompt. Review the publisher's license and choose installation options yourself.

The installer and driver are not bundled. There is no silent installation or automatic license acceptance. Cancellation, declined elevation or failure leaves capture off while screen OCR remains available. A required reboot leaves the meter off and does not restart Windows; restart when convenient, then enable the meter again. Otherwise Sentinel rechecks capture components before retrying its worker. Capture permissions can still prevent readings. Manual installation from [the publisher's download page](https://npcap.com/#download) is also available.

The meter displays captured damage, DPS and share. Names arrive separately; keep capture running through login or an area change if names are pending. Its default measurement aggregates captured actors and targets and may include non-party actors. Ordinary boss deaths do not guarantee a separate per-boss counter. Current EU damage accuracy remains unverified.

## Coverage and development status

The catalog contains **1,002 profiles: 223 with some warning support and 779 identity-only**. The reviewed world/high-GS subset has **137 profiles**, with **72** supporting some warnings and **65** remaining identity-only. These counts and the 550/209 timing inventory describe source coverage, not complete phases, every boss mechanic or verified live recognition.

**Unfinished Beta.** Gameplay validation is pending; compilation and package integrity have been checked. These checks do not establish in-game warning behavior or cast-end accuracy. Full wave sequences and recurring encounter schedules remain unfinished.

## Install and use

Extract the complete archive into its own writable folder and launch **Start-AION-Sentinel.cmd**. Keep all runtime folders, models and notices together. Run the English game in windowed or borderless mode, keep target/minimap headings visible, enable **Combat HUD**, choose **Start observation** and bring the game to the foreground. Enable the meter separately if wanted.

**F7:** Combat HUD · **F8:** Start / Stop observation · **F9:** Reset encounter

Archive: `AION-Sentinel-0.6.8-beta-windows-x64.7z` · **95,352,628 bytes (95.35 MB / 90.94 MiB)** · **430 extracted files**. The archive is below the strict **100,000,000-byte** limit.

SHA-256: `14eec381b0baec79440c56560f904a4f03cd05af0af2a20241a1c0343bdc9287`

## Downloads and support

[0.6.8 release and documentation](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases/tag/v0.6.8) · [Project](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-) · [Issues](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/issues)

The package's internal integrity signatures are separate from Windows Authenticode signing. AION Sentinel is independent of NCSOFT and Deadly Boss Mods; official approval and account-safety guarantees have not been established.
