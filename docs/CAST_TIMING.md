# Cast timing — Sentinel 0.6.10 Unfinished Beta

Sentinel connects reviewed static skill facts to passive measurements of a currently visible target cast. A measured cast-end estimate can appear on the combat HUD and produce an estimated cast-end heads-up. Complete wave sequences, individual wave impacts and recurring encounter schedules remain unavailable.

## Static timing reference

The packaged `skill_timing_reference.json` records 550 accepted skill IDs and their associations with 209 profiles, covering 859 grouped rule associations. These are source-inventory counts, not 550 verified live cast bars or 209 complete fight timelines. The reference preserves exact NPC `ActiveSkillList` ownership, English labels, raw casting/cooldown fields, configured visibility and range-warning facts. NPC ownership must belong to an actual target template. Same-name candidates are eligible only when every owned candidate belongs to one common warning rule; the group retains all its IDs and leaves its unique ID absent. A same name across different rules, encounters or effects remains ambiguous. An explicit verified structured template ID can narrow the group; OCR does not supply that template identity.

The reference pins hashes for the English Steam name, NPC, skill and skill-range domains and the warning asset. A local static DLL review confirms field mappings and the `EHideSkillGauge` enum. Those source facts do not establish compatibility with the current EU client or whether a particular cast is visible.

`CastingTime` and `NeedCoolTime` have no proved unit in the supplied records or reviewed export path. Their converted millisecond/second fields remain absent values. A configured cooldown also does not establish when an NPC's behavior tree chooses to cast again. These raw values supply neither the live cast clock nor a repeat interval.

Configured `RangeNoticePreviousTime` is retained as `notice_lead_ms`; configured `WideCastingAlertTime` is retained as `wide_alert_ms`, following the reviewed export labels. These are reference warning settings. A range-warning lead alone does not identify an observed effect's start, its impact or a future wave.

For Bakarma's owned `Wave of Death` skill:

| Field | Stored fact | Operational meaning |
|---|---|---|
| Skill ID | `1800655` | Static identity, associated with exact source NPC owners |
| `CastingTime` | `18000` raw | No verified conversion to seconds |
| `NeedCoolTime` | `1000` raw | No repeat schedule inferred |
| Range record | `18006506` | Configured range metadata |
| `notice_lead_ms` | `5000`, equivalent to 5 seconds | Static range-warning lead; does not start a clock |
| `HideSkillGauge` | `3` / `All` | Configured gauge hiding can prevent a visible cast measurement |
| `HideSkillfloater` | `true` | Configured text hiding can prevent a recognized cue |

Hidden metadata never creates a synthetic bar. If the current client actually displays usable cast evidence, Sentinel can observe that evidence. Without it, the corresponding countdown remains absent.

## Passive screen synchronization

Automatic HUD discovery supplies a small cue crop beneath the confirmed target header. Timing uses that original target-anchored crop even if an expert has selected a separate mechanic-text crop. It requires the active profile's exact English target name and an owned skill label associated with one eligible warning rule. A skill name alone never establishes the cast's start or elapsed duration. Broadcast and player-debuff text use separate channels and never supply this target-cast clock.

An explicit neighboring time such as `3.2 s` or `3.2 sec` can supply remaining seconds. Bare numbers, HP percentages and health fractions do not. The parser accepts a separate adjacent timer box or the exact skill name followed by an explicit seconds suffix. Ambiguous labels or multiple adjacent timers supply no measurement.

A conservative optional image check can measure a single outlined gold/blue horizontal cast track directly below the skill text. It requires a continuous filled segment and a dark unfilled segment. Red/green health bars, full tracks, multiple tracks and uncertain geometry are rejected. This check is deliberately narrow; other HUD appearances can leave the countdown absent.

Two independent, temporally consistent screen measurements are required before a timing record is emitted. OCR-cache reuse, identical images and unchanged time/progress values do not become new timing samples. The engine validates the resulting stream again. Explicit remaining seconds must decrease consistently with capture time. A fraction-only cast track needs at least three changing engine samples spanning at least 0.35 seconds, enough movement and a stable measured slope before it yields a duration estimate. The duration comes from those observations, not raw `CastingTime`.

The measured fraction or remaining seconds supports joining an already running cast. Sentinel does not backdate a cast from the first appearance of its name. The HUD labels the result as an estimate. Expert **Cues** provides **Cast-end heads-up** separately from repeat timers; its default is 3 seconds, and zero disables that heads-up. The static 5-second Bakarma range notice does not automatically become this threshold or a jump call.

## Identity, interruptions and recordings

Boss/profile changes, window changes, focus loss, reset and stopping observation clear cast state. Confirmed readable non-cast cue text can emit an idle record after independent confirmation. Empty or failed OCR is not proof that a cast ended. A cast estimate expires when fresh timing measurements stop for more than 2.5 seconds or its measured deadline passes. Frozen frames never keep it alive.

Ordinary observation journals retain accepted `cast_timing` records with source, confidence, capture timestamp and independent-sample evidence. Replay validates those records. Screen measurement sources are `screen_remaining` and `screen_progress`; an active record identifies the skill and includes its measured seconds or fraction. An idle record contains no active skill or measurement. Missing evidence omits the field.

An external structured observer can instead provide an owned `casting_skill_id` together with `casting_remaining_seconds` or `casting_progress`. It must supply fresh, trustworthy measurements. Damage-hit IDs and static skill IDs by themselves do not start a clock. See [structured observations](STRUCTURED_OBSERVATIONS.md).

## Validation status

This integration is **Unfinished Beta**. No new application, executable, OCR, UI, functional, unit, integration or live-game tests were run for 0.6.10. Source syntax, compilation and package integrity checks are structural evidence only. Visibility, HUD coverage, cast-end accuracy and live warning behavior remain to be established in the game. Demos use generated data and do not establish wave timing.

## Local recurrence estimates

The separate learner is a preparatory model for intervals between accepted observed onsets. It requires exact encounter, NPC/map, difficulty and confirmed phase identity, at least five intervals across three completed live attempts, and a stable interval spread within 15%. It remains inactive in the current UI: screen OCR leaves phase unknown, and the generic local JSONL feed is not verified live training evidence. A future verified provider must supply both fresh measurements and confirmed phase context. Model estimates remain local and expire with stale observations or a context change. They do not convert raw cooldowns, reconstruct a full timeline or predict individual wave impacts.
