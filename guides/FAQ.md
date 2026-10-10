# FAQ and troubleshooting

Created by **Neophrythe & Dr.Tatsu**.

## Is 0.6.8 fully verified?

It is an Unfinished Beta with gameplay validation pending. Compilation, signed-file integrity and archive roundtrips have been checked; these do not validate application behavior, guided setup, cast-end accuracy or live fights.

## Do all bosses have warnings?

No. The reviewed identity catalog is broader than its mechanic coverage. There are 1,002 profiles, 223 with some warning support and 779 with identity metadata only. The world/high-GS target subset has 137 profiles, of which 65 remain identity-only. See [coverage](COVERAGE.md).

## Why is the HUD empty?

Enable Combat HUD and observation, then bring AION2 forward. The observer needs visible English target and location labels. Normal enemies, missing labels, unresolved variants or absent skill text can keep it quiet. An identity-only boss has no generated mechanic warnings.

## Why is there no cast countdown?

A skill name alone does not start a clock. Automatic timing requires a uniquely associated owned skill under the confirmed target header and explicit remaining seconds or a supported changing cast bar. Fresh, consistent independent samples sustain the estimate; hidden, ambiguous or frozen cues do not. Automatic HUD discovery must be active; manual-region mode does not supply automatic target-cast timing. See [cast timing](../docs/CAST_TIMING.md).

## Does the countdown show the next wave or jump moment?

It estimates the currently observed cast's end. It does not time individual waves, player-relative jump moments or recurring fight sequences. Raw casting and cooldown values remain reference data. Expert **Cast-end heads-up (s)** defaults to 3 seconds and accepts 0–30 seconds; it is separate from configured range-warning metadata.

## Do I need to select a boss or screen region?

The default mode selects compatible profiles and standard HUD regions automatically. Expert tools remain available for a customized HUD. Missing mechanics or hidden skill labels cannot be solved by choosing a different profile at random.

## The meter does not start

Enable **Damage meter**. If Npcap is absent, Sentinel offers **Set up Npcap**: with your consent, it downloads the fixed official Npcap 1.89 installer, checks the pinned SHA-256 and publisher signature, then opens its visible installer and the normal Windows elevation prompt. Review the license and options yourself. An existing installation skips this helper; the driver and installer are not bundled, and installation is not silent.

Cancelling, declining elevation or installation failure leaves capture off and screen OCR available. If a reboot is required, restart Windows when convenient and enable the meter afterward; Sentinel does not restart the computer. Otherwise, it rechecks capture components and retries the worker. If the installed driver cannot capture, use **Advanced → Expert controls → Damage meter → Capture setup / help**, resolve the reported permission problem and enable the meter again. Keep the complete `meter` folder beside the application. No separate meter application or service key is required.

## Why are player names missing?

Names and damage arrive in separate records. Starting capture after login can miss names. Keep it enabled during an area change or login. Matching records update the corresponding player ID; unrelated anonymous rows are not assigned a guessed name.

## Is the meter party-only or reset for every boss?

It displays captured actors and aggregate run damage. Non-party players may appear. Existing decoded run-boundary heuristics can reset a run; ordinary boss deaths do not guarantee a separate per-boss counter. Off/on begins a fresh capture worker and measurement.

## The executable will not start

Extract every file and try the included `Start-AION-Sentinel.cmd`. It reports missing runtime files and early startup errors. Internal signatures are not Windows Authenticode publisher signing. Download a fresh complete archive if files were modified or removed.

## Does it control the game?

No. The warning observer reads the screen; the optional meter observes captured combat records. This release does not inject into the game, change game files or automate gameplay. Sentinel is independent of NCSOFT and Deadly Boss Mods; official approval, detection guarantees and account-safety guarantees have not been established.

## Where do I get help?

Open a [bug report](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/issues/new/choose) with your release version, Windows version, relevant visible message and steps to reproduce. Keep account credentials and private capture files out of public reports.
