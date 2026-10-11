# Sentinel 0.6.10 — Unfinished Beta

Created by **Neophrythe & Dr.Tatsu**. Windows x64, AION 2 EU / International, English client.

This release combines the 0.6.9 encounter and meter improvements with compact, sourced combat research. It retains the three beginner controls: **Combat HUD**, **Start / Stop observation** and **Damage meter**.

- **88 published mechanic references from 16 sources**, associated with **42 catalog profiles** where identity and instance match. The expert encounter guide shows reactions, approximate HP ranges, timing types, source links and source limitations. Shortened guide titles are reference associations; they do not become OCR aliases.
- **48 typed timing fields** distinguish cast duration, effect lifetime, windup, telegraph lead and hit spacing. These are publisher claims, with their original quality and difficulty context. They never supply automatic recurrence, phase transitions or player-relative jump clocks.
- Exact owned English skill rules can display associated research notes. Existing curated responses take precedence. A compatible additional explicit-label response upgrades unchanged generated wording; custom messages and disabled rules remain respected.
- Aggregate public EU log identity evidence is visible for **137 targeted profiles**. Logs can identify a boss variant without supplying a mechanic timeline. No player logs, account data, GPL implementation or original bot binaries are included.
- Automatic profile synchronization is now retained in recording, replay and descriptive timing analysis. Cast-observation state is reset when synchronized settings change.

Included changes since the published 0.6.8 release:

- Separate broadcast and player-debuff observations: 3 broadcast mechanics, 9 debuff mechanics and 14 exact English labels across 10 encounter identities. Exact context and fresh independent confirmations are required.
- Safer handling of multiple owned skill IDs with the same name, plus improved avoidable-wipe priorities.
- Independent damage HUD visibility, lock, scale, opacity and recenter controls; captured target selection and confirmed-party filtering.
- Local history retention up to 100 reports within 32 MiB. Attempt and run reports overlap and must not be summed.
- Saved HUD layouts persist across automatic profile changes; stale OCR does not confirm a new context.

The reviewed static cast inventory remains 550 skill IDs across 209 profiles. Complete measured EU phase schedules remain unavailable. Many catalog entries provide identity only, and supported warning profiles can still lack mechanics. Hidden cast bars, unknown party names, unsupported HUD layouts and ambiguous encounters can leave information absent. The preparatory recurrence learner remains inactive without a verified phase provider.

The package uses the unchanged 0.6.9 native meter payload, with its exact hash recorded, and a newly compiled 0.6.10 application. Native compilation, the own-file RSA integrity manifest and lossless archive checks protect distribution integrity; this is not Windows Authenticode signing. Gameplay validation remains pending. No new application, UI, OCR, unit, integration or live-game execution is performed for this release.

Extract the entire package to a writable folder and launch **AION-Sentinel.exe** or **Start-AION-Sentinel.cmd**. Keep `_internal`, `meter`, models and notices together. Npcap is needed only for the optional meter; guided setup uses the separate official installer with user consent.

Archive: `AION-Sentinel-0.6.10-beta-windows-x64.7z` · **95,292,144 bytes** (95.29 MB / 90.88 MiB), 433 files. Strict limit: 100,000,000 bytes.

SHA-256: `8aa341143ef8ce79a0d585ca4acc409b6992c9c083f33b46de4db1fad1cc0743`
