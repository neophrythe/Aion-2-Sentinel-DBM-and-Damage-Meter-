# FAQ and troubleshooting

## Is 0.6.6 fully verified?

No. It is an untested implementation preview. Compilation, file signatures and archive integrity were checked; application behavior and live fights were not tested for this build.

## Do all bosses have warnings?

No. The reviewed identity catalog is broader than its mechanic coverage. There are 1,002 profiles, 223 with some warning support and 779 with identity metadata only. The world/high-GS target subset has 137 profiles, of which 65 remain identity-only. See [coverage](COVERAGE.md).

## Why is the HUD empty?

Enable Combat HUD and observation, then bring AION2 forward. The observer needs visible English target and location labels. Normal enemies, missing labels, unresolved variants or absent skill text can keep it quiet. An identity-only boss has no generated mechanic warnings.

## Do I need to select a boss or screen region?

The default mode selects compatible profiles and standard HUD regions automatically. Expert tools remain available for a customized HUD. Missing mechanics or hidden skill labels cannot be solved by choosing a different profile at random.

## The meter does not start

Check that Npcap is installed, Windows allows capture and the complete `meter` folder was extracted. Read the displayed error, correct the prerequisite and toggle Damage meter off/on. No separate meter application or service key is required.

## Why are player names missing?

Names and damage arrive in separate records. Starting capture after login can miss names. Keep it enabled during an area change or login. Matching records update the corresponding player ID; unrelated anonymous rows are not assigned a guessed name.

## Is the meter party-only or reset for every boss?

It displays captured actors and aggregate run damage. Non-party players may appear. Existing decoded run-boundary heuristics can reset a run; ordinary boss deaths do not guarantee a separate per-boss counter. Off/on begins a fresh capture worker and measurement.

## The executable will not start

Extract every file and try the included `Start-AION-Sentinel.cmd`. It reports missing runtime files and early startup errors. Internal signatures are not Windows Authenticode publisher signing. Download a fresh complete archive if files were modified or removed.

## Does it control the game?

No. The warning observer reads the screen; the optional meter observes captured combat records. This release does not inject into the game, change game files or automate gameplay. No detection or account-safety guarantee is made.

## Where do I get help?

Open a [bug report](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/issues/new/choose) with your release version, Windows version, relevant visible message and steps to reproduce. Keep account credentials and private capture files out of public reports.
