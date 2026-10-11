# Damage meter accuracy — 0.6.13 Unfinished Beta

Created by **Neophrythe & Dr.Tatsu**. This revision addresses the source findings
in METER_COMPETITOR_COMPARISON_2026-10-11.md; that document describes the earlier
0.6.12 baseline, not the new measurement behavior.

## Measurement

All display modes use selected damage from the first through the last retained
hit, with a common divisor of at least one second. An idle display does not lower
DPS. A resumed phase includes its entire intervening pause. Manual finish and
automatic boss completion keep the same first-to-last measurement rule.
The exported interval remains the actual measured span; dps_divisor_seconds
records its one-second floor separately. No artificial damage multiplier is used.

Automatic boss attempts count only that boss. Counter/all-target mode includes
other targets. Both the HUD and control window identify this scope; attempts,
run totals and counter totals overlap and must not be added together.

## Attribution

Minimal numeric summon-attack compatibility IDs are derived from the pinned
MIT reference f59fcfe3. Display-name catalogs and game images are not included.
An unresolved, recognised unspawned summon can have an **Unassigned summon**
row. A unique-class fallback requires a confirmed owner name and an unambiguous
observed party-class roster or own character record. Unknown same-class party
members prevent choosing the one member whose runtime ID happens to be known.
This is observed-context inference, not an authoritative game ownership API.
Explicit spawn/cast ownership remains supported.

Later ownership moves provisional contributions to the owner across the
current run, counter, boss aggregates and up to 128 retained current-run reports,
including their time bins. It preserves totals, timestamps, skill damage and
direct hit/critical counts; repeat records are idempotent. Provisional credits
carry an entity generation. A new spawn prevents a reused entity ID from moving
older contributions. Epoch-zero ordinary player damage is never transferred.
Counter reset leaves old counter contributions cleared; a run reset does not
reattribute archived previous-run contributions.

## Protocol

The MIT 645f4b7d correction classifies an NPC effect triggered by a player hit as
the target's self-heal. The published fixture retains 31,724 player damage and
excludes the 122,788 self-heal.

Compact 0x02 damage ticks may omit a trailing skill ID; a valid player-class
effect identifies their numeric skill. Exact heal/buff forms and numeric
heal/buff classifications do not enter damage totals. Ticks add damage while
remaining separate from direct-hit/critical counts.

The existing MIT bundle decoder supports nesting through four compressed
levels. Each input has a shared eight-MiB expansion budget and a bounded
inner-frame count. Excessive nesting, malformed lengths and truncated layouts
fail closed. Extra-hit tails are not added again to a main amount that already
contains them. These format improvements do not establish complete current-EU
coverage or prove the exact cause of the reported Deus difference.

## Verification

Focused cases include published MIT frames, compact ticks, self-healing,
metadata-only late ownership, duplicate evidence, actor reuse, counter/run
reset, corrected report timelines, short fights, idle DPS, resumed phases and
nested compression. Actual counts, native SHA-256 and current source hashes are
recorded in the release's offline evidence. Current live encounter agreement
and the complete frozen application's gameplay behavior remain pending.

Sources: [MIT spirit correction](https://github.com/SkeeveAN/Aion-DPS-Meter/commit/f59fcfe3b7815a335ae8a944e99b94ac507093fa),
[MIT self-heal correction](https://github.com/SkeeveAN/Aion-DPS-Meter/commit/645f4b7dd6f4f52247ebba55d94e334799b84ded).
