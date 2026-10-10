# Boss warnings — Sentinel 0.6.8 Unfinished Beta

Created by **Neophrythe & Dr.Tatsu**.

The 0.6.8 integration connects static skill timing facts to measured visible target casts. No new application, functional, unit, integration or live tests were run. See [current release status](RELEASE_0.6.8_BETA.md) and [cast timing](CAST_TIMING.md). The baseline warning asset is retained from 0.6.5; its historical checks do not validate this preview.

New in 0.6.6: world-boss classification and scopes; explicit >=1400-GS reference-map filters; published guide responses joined only to already owned exact English skill text; a Tetrata 50%-HP reinforcement-wave reference guarded by template 2340158 and eight exact maps. See [target registry](ENCOUNTER_TARGETS.md) and [guide evidence](ENCOUNTER_GUIDES.md). Approximate HP ranges, historical Ludra and unbound phases remain inactive.

Sentinel builds default warnings from the reviewed English Steam NPC/skill facts and the pinned public mechanic catalog. This expands coverage; it is not a complete, live-verified DBM timeline for every enemy.

## What loads automatically

- 859 grouped English skill-text rules across 209 profiles, representing 277 normalized labels and 550 accepted static skill IDs. The same owned label can produce separate rules for multiple profiles. A rule fires after two fresh matching observations of a complete OCR line in the boss cue region. Generic `Attack`, basic attacks, blank names, conflicting labels and internal/debug strings are excluded.
- All 54 public source HP thresholds across 23 profiles, presented as reference hints. A phase crossing needs two above-threshold observations followed by two nonincreasing observations at or below it. A single low OCR reading and joining a fight already below the threshold do not fire a phase warning.
- Three additional dungeon-source HP hints for the Central Abyss Fusion Reactor: 90%, 60% and 30%. Both map `600082` and an unambiguous candidate/observed template `2301008` are required. Unknown or conflicting map/template evidence keeps these hints silent.
- Prepared Draupnir text cues for waves, stagger, stagger success and water hazards. Owned `Wave of Death` and `Winding Waterspout` labels have guide-based response messages. These remain observed-text response rules. Separate passive cast measurements can add a cast-end estimate, while individual wave impacts and jump timestamps remain unavailable.

The baseline warning asset accounts for all 1,002 profiles. It supplies some HP or skill-text warning support to **222 profiles**; **780 profiles have identity recognition only in that baseline**. Including the separately scoped source-event addition, the current combined catalog has **223 profiles with some warning support and 779 identity-only profiles**. Skill and HP profile counts overlap. The 54 public thresholds and three separately scoped dungeon hints supply **57 HP reference rules**. A supported profile can still lack important mechanics. None of these counts establishes full live encounter coverage.

## Controls and upgrades

In **Setup**, `Warn on recognized boss skill text` switches generated skill-text warnings on or off. Each individual warning can also be edited or disabled in **Cues**. Source HP hints have their own switch. Cues exposes complete-line versus phrase matching and the number of confirming observations.

Fresh installations load the generated default profile before observation starts. Saved user rules, messages, disabled choices, estimates and learned images are preserved; newly available rules are appended without duplicate IDs. Unmodified empty editor slots can be replaced by real rules. The latest source correction removes the old Afflicted Bakarma phase association and places those three facts on Transcendent Bakarma. Custom edits survive this correction.

**Boss library** shows HP hints, skill-text rules and unbound phase entries separately for every profile. Select a profile to see its warning status and inspect local GameData. `Export warning coverage` saves a machine-readable coverage report. This makes profiles without active rules visible before a fight.

## Evidence and limits

Static NPC ownership establishes which labels belong to a candidate boss; it does not prove that the current EU game displays those labels. All 550 accepted skill IDs have at least one configured gauge/floater hiding flag: raw `HideSkillGauge` is 3 for 465 IDs and 0 for 85, and all 550 have `HideSkillfloater=true`. These raw settings do not establish whether the text appears elsewhere in the UI. A generated rule must actually observe its text; an absent label produces no warning. Static skill IDs are retained as reference metadata and are never turned into unverified live cast IDs. The asset records zero live-verified profiles.

The 263 public mechanic facts still have 209 phase triggers without a detectable cue and no explicit fight-second timings. Raw cast/cooldown/groggy settings are not converted into countdowns. User-configured repeat timers remain estimates. Matching a skill label may happen during or after an attack; the label alone establishes no clock or advance warning.

The separate timing reference records 550 accepted skill IDs across 209 profiles with exact NPC ownership, raw configured fields, range notice leads and visibility. Raw `CastingTime` and `NeedCoolTime` have no proved unit and remain outside the live clock. For Bakarma `Wave of Death`, the reviewed `notice_lead_ms=5000` is a static 5-second range-warning setting, not a synchronized wave deadline. `wide_alert_ms` similarly records a configured warning value.

Automatic cast timing requires a uniquely associated exact owned skill under the confirmed target header and an explicit neighboring seconds value or a conservatively detected changing cast bar. Cache reuse, identical frames and unchanged measurements do not count as new samples. The engine checks decreasing seconds or learns a stable slope from several progress samples; its HUD result and cast-end heads-up remain estimates. Gauge/text hiding, ambiguous IDs and unsupported bar shapes can leave the countdown absent. No individual wave offsets, jump moments or repeat schedules are generated from this data. See [cast measurement and limits](CAST_TIMING.md).

The deeper dungeon audit inspected 733 records containing 703 `HpRemaining` rows, with 608 distinct serialized HP event objects, plus phase, behavior-tree, wave and broadcast actions. This deduplicated event count is not a boss count. Most matching HP actions summon healing orbs, change dialogue or advance quests. Those are not added as boss phases. No HP objective directly invokes `NpcChangePhase`; the two HP-linked `ChangeBT` actions concern companion NPCs. A spawn-wave directive does not establish a pressure-wave attack. The three directly linked reactor reinforcement chains and the separately proven Tetrata 50%-HP reinforcement graph are retained as reference hints. Raw HP strings have no explicit unit field and live behavior remains unverified. The source gates these chains on dungeon state `Process`, which Sentinel does not independently observe: the overlay reports an HP reference, not proof that the dungeon action ran.

The damage meter does not provide a verified pre-impact boss-cast producer. Damage-hit skill IDs are not cast-start events, and highest observed HP is not maximum HP. These values are not substituted for missing encounter observations.

## Sources and reproducibility

The original catalog asset remains unchanged. Runtime mechanic associations come from the MIT-licensed [Aion-DPS-Meter mechanic source](https://github.com/SkeeveAN/Aion-DPS-Meter/blob/25b6d5d1a62fededfbdbe67ab71c687f3820d8fb/Backend/src/data/aion2/mechanics.json). The copied asset retains the complete license, Git blob pins and SHA-256 values. All 54 newly listed public world-boss names already exist in Sentinel's current identity profiles.

`research/scripts/build_sentinel_warning_data.py` checks every file in the supplied 16-file English Steam manifest, validates decoded hashes and derives the warning asset deterministically. `aion_sentinel/assets/boss_warning_reference.json` contains source ownership, rejected-label reasons and per-profile coverage. The dungeon event audit is `research/BOSS_WARNING_DUNGEON_EVIDENCE_2026-10-09.json`.

The Draupnir response facts are paraphrased from the [Gamers Together guide](https://gamerstogether.cz/en/aion-2-draupnir-dungeon-guide/) and [Draupnir guide](https://aion2maps.com/guides/draupnir/). No guide text, diagrams or artwork are copied.

The existing `--boss-warnings-test --output report.json` development tool is available for later verification. It was not executed for 0.6.8. Prior 0.6.5 synthetic and UI checks are historical evidence only; neither they nor compilation establish this build's behavior.
