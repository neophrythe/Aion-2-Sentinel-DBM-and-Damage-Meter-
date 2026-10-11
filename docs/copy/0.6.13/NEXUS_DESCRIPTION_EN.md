# AION Sentinel - Boss Warnings + Damage Meter

Created by **Neophrythe & Dr.Tatsu**.

**0.6.13 - Unfinished Beta. Active development - gameplay validation pending.**

AION Sentinel brings DBM-inspired boss warnings and an optional damage meter to the **AION 2 EU / International English PC client**. It runs alongside the game as a separate **Windows 10/11 x64** desktop companion with a movable combat HUD.

## New in 0.6.13

DPS now uses a shared first-to-last hit interval with a one-second minimum. Recognised unresolved summon damage is retained and can be merged later with generation-scoped ownership. Compact damage ticks, bounded nested packets and NPC self-heal filtering are improved. Boss-only and all-target scopes are labelled clearly. Deus recognition, capture continuity, automatic boss attempts and bounded history improvements are included. 182 Python checks and 88 native worker assertions passed on this build. Complete frozen-application gameplay and the reported live DPS difference still require a matching encounter comparison.

## Three controls to begin

- **Combat HUD:** show or hide the boss-warning overlay.
- **Start / Stop observation:** follow visible English target and location text automatically.
- **Damage meter:** start or stop the bundled passive capture worker and its separate damage HUD.

Compatible encounter profiles and standard HUD regions are selected automatically. Normal enemies stay quiet. Observation and capture stop independently through the beginner controls and F8. Optional expert tools remain available for custom HUD layouts; manual-region mode does not supply automatic target-cast timing.

Movable action warnings, Imminent and Upcoming bars, local OCR models and an available English Windows speech voice remain included. Timer estimates retain their **~** marker.

## Guided setup for the optional meter

If Npcap is already installed, Sentinel skips setup. Otherwise, enabling **Damage meter** offers **Set up Npcap**. With your consent, Sentinel downloads the fixed **Npcap 1.89** installer from its official publisher, checks the pinned SHA-256 and publisher signature, then opens the normal visible installer and Windows elevation prompt. Review the publisher's license and choose installation options yourself.

The installer and driver are not bundled. There is no silent installation or automatic license acceptance. Cancellation, declined elevation or failure leaves capture off while screen OCR remains available. A required reboot leaves the meter off and does not restart Windows; restart when convenient, then enable the meter again. Otherwise Sentinel rechecks capture components before retrying its worker. Capture permissions can still prevent readings. Manual installation from [the publisher's download page](https://npcap.com/#download) is also available.

The meter displays captured damage, DPS and share. Names arrive separately; keep capture running through login or an area change if names are pending. Automatic boss attempts count the boss target only. All targets keeps a separate counter including adds; captured non-party actors can be present. DPS uses a shared first-to-last damage span with a one-second floor. Idle display time does not reduce DPS; a resumed phase includes its intervening pause. Captured targets and confirmed party members can be filtered in Expert controls. Local history keeps up to 100 reports within 32 MiB; attempt and run reports overlap. Current EU damage accuracy remains unverified.

## Coverage and development status

The catalog contains **1,002 profile identities**; mechanic coverage remains partial. The reviewed world/high-GS subset has **137 profiles**. Research identity counts do not establish cast or phase coverage. These counts and the 550/209 timing inventory describe source coverage, not complete phases, every boss mechanic or verified live recognition.

**Unfinished Beta.** Gameplay validation is pending; focused offline checks, compilation and package integrity have been checked. These checks do not establish in-game warning behavior or cast-end accuracy. Full wave sequences and recurring encounter schedules remain unfinished.

## Install and use

Extract the complete archive into its own writable folder and launch **Start-AION-Sentinel.cmd**. Keep all runtime folders, models and notices together. Run the English game in windowed or borderless mode, keep target/minimap headings visible, enable **Combat HUD**, choose **Start observation** and bring the game to the foreground. Enable the meter separately if wanted.

**F7:** Combat HUD | **F8:** Start / Stop observation | **F9:** Reset encounter

Archive: AION-Sentinel-0.6.13-beta-windows-x64.7z | **95,533,011 bytes** (95.53 MB / 91.11 MiB), 442 files.

SHA-256: `b90481196a5d8e6b045d80c8a33db459127f9c3d5082536e31c74d8e3a472961`

## Downloads and support

[0.6.13 release and documentation](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases/tag/v0.6.13) | [Project](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-) | [Issues](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/issues)

The package's internal integrity signatures are separate from Windows Authenticode signing. AION Sentinel is independent of NCSOFT and Deadly Boss Mods; official approval and account-safety guarantees have not been established.
