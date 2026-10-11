# Deus recognition audit for 0.6.12

This audit concerns the English EU/International scope and passive DBM observation.
It records local source facts and an offline recognition correction. It does not
establish live gameplay correctness, exact cast durations, phase schedules, or
the cause of a particular player's missing warnings without that observation.

## Concrete recognition defect and correction

The regular `Deus Research Base` has one `unspecified` catalog profile per boss:
`DeusCenter/atiel`, `DeusCenter/gelcos`, and `DeusCenter/nazmun`.
There are no Explore/Conquest profile pairs for these names in the shipped
catalog. Missing difficulty text therefore does not itself make these profiles
ambiguous.

`world_identity_reference.json` also contains same-name nonattackable objects.
Atiel has 18 `NpcType: 4`, `NpcSubType: 7`, `bCanBeAttacked: false` variants at
level 20; Gelcos has three at level 20. Nazmun has three at level 45, IDs
`2920505`, `2920506`, and `2920507`. All these objects have empty map associations.
Previously `eligible_candidates()` retained them as possible combat targets and
rejected the complete boss candidate even with confirmed Deus location. A
leading level helped Atiel/Gelcos but could not separate level-45 Nazmun objects.

The correction excludes only explicitly nonattackable Type 4 objects from
competing identities when no exact target template was observed. Ordinary
monsters, attackable objects, missing/uncertain flags, level constraints, and map
constraints remain negative evidence. An exact template identifying a Type 4
object remains rejected. An empty set after excluding objects remains rejected.
No profile, warning trigger, or timing fact was changed.

Fresh native template identities remain useful: the base IDs `2300601` (Atiel),
`2300616` (Gelcos), and `2300615` (Nazmun) are exact local boss associations.
They require the existing independent visible-target correlation and freshness
checks; nearby NPC activity does not select a target or establish player location.

## Existing warning coverage

The counts below are local source coverage, not a report of live validation.
All HP rows remain unverified source reference hints and require actual observed
HP crossing evidence. Named skill rows require two fresh independent exact
English text observations.

| Regular Deus boss | Owned English skill cues | Source HP hints | Remaining unbound source phases |
| --- | --- | --- | --- |
| Atiel | `Morphic World` | Tether to boss at 50%; Morphic World at 25% | 10 |
| Gelcos | None: linked names are generic/basic attacks | Drag field at 50%; puddles erupt at 25% | 11 |
| Nazmun | `A One! And a Two!`, `Bomb Drop`, `Drone Strike`, `Evasive Maneuver`, `Laser Bombardment`, `Trap Install`, `Ultra Laser` | Donut/time bomb at 75% | 11 |

Atiel additionally has two published broadcast cues in the existing guide
integration: `All will collapse and perish!` and `You cannot escape from me!`.
They require the broadcast channel, the exact compatible boss/instance context,
and two independent observations. A skill label cannot substitute for broadcast
text. The existing `Morphic World` response can also use the published stagger
advice through its exact local NPC-owned skill join.

All owned Atiel/Nazmun skill cue rows carry `configured_hidden_skill_ids`.
Static visibility settings make missing visible labels a plausible limitation;
they do not prove that every runtime cast label is absent. No countdown or
repeating phase was inferred from those settings.

## Consumed Deus is a different encounter

`Consumed Deus Research Base` has three separate `unspecified` profiles:
`BlasphemyLab/lab-director-zylus`, `BlasphemyLab/overseer-gromkas`, and
`BlasphemyLab/prideful-atiel`. They have no exact matching English NPC rows in
the pinned GameData reference, no owned skill cues, and no HP hints. Their four,
two, and six source phase rows respectively have no observable English binding
and remain disabled. These profiles are currently identity-only.

The guide's `Xailus` and `Arrogant Atiel` names are not confirmed catalog aliases;
their mechanics and the Consumed Gromkas guide are marked `kr_tw_reference`.
They are not promoted into EU/International triggers. The existing location
matcher consumes the longer `Consumed Deus Research Base` label before its
nested `Deus Research Base` label and keeps their allowed profiles separate.
The user's spelling `Dues` is not a supplied location alias.

## Remaining observation gates and limits

Automatic DBM still requires two independent target-name observations and a
confirmed compatible location when location tracking is active. Pending,
conflicting, or expired location pauses warnings before profile selection.
Automatic HUD discovery can also pause while its location region is unresolved.
The rank fix does not bypass these observation gates.

Shared-variant mode currently excludes HP hints and requires actual compatible
variant pairs. That policy is unrelated to the regular Deus defect, whose
profiles already have unique `unspecified` variants. No common-HP policy change
was made here. Gear-score gating is not present on these six profile records.
Restricted expert scopes such as `world_bosses` or `priority_targets` can filter
these ordinary dungeon bosses; the simplified automatic scope is `all_elites`.

Evidence: `aion_sentinel/assets/boss_library.json`,
`world_identity_reference.json`, `game_data_reference.json`,
`boss_warning_reference.json`, and `encounter_guide_reference.json`; selection in
`special.py`, `context.py`, `automatic_mode.py`, and `ui.py`. Focused offline
regressions are in `tests/test_deus_recognition.py`. Live Deus behavior still
needs real encounter observations, especially location/HUD recognition and
whether the accepted English cue text is actually visible.
