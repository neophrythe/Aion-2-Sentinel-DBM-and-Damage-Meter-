# Encounter target registry — Sentinel 0.6.6, Unfinished Beta

The registry identifies every world-boss entry in the reviewed public list and every named, source-classified boss candidate on verified instance maps whose explicit entrance gear requirement is at least 1400. It describes identity and scope. It does not fill missing mechanics, guarantee live recognition or claim that every listed map is available in the current EU client.

No new unit, functional, integration or live tests were run for this implementation, as requested. Source integrity checks, JSON generation and Python syntax compilation are separate structural checks. The deferred tests are in `tests/test_target_registry.py`.

## Reviewed scope

| Source scope | Entries / profiles | Current warning support |
|---|---|---|
| Public world-boss groups | 54 entries, 51 distinct English profiles, 56 verified NPC templates | 26 profiles with 111 existing skill-text rules; 25 distinct profiles remain identity-only |
| Public modes with explicit item level >= 1400 | Six instance variants, 21 boss entries | Joined by actual public profile key; no guessed mode translation |
| Steam instance maps with explicit entrance item level >= 1400 | 83 map variants, 86 associated existing profiles | 46 profiles currently have some skill or HP reference support |
| Combined target registry | 137 existing profiles, 260 source template IDs | 72 profiles with some existing warning support; 65 identity-only |

The world groups contain 24 Verteron, 24 Altgard and six Abyss entries. Silent Dartan, Soul Ruler Kashapa and High Commander Lagta each appear in both Verteron and Altgard, accounting for 54 entries but only 51 names. The six Abyss profiles currently have identity metadata only. No world profile has verified phase bindings or HP warning thresholds.

The registry marks world profiles as `world_boss` while preserving their original eligibility variants. The runtime must continue to reject summon/normal variants even in a world-boss scope. Black Tentacle Lawa and Eternal Gartua have same-name summon candidates; unknown map links remain negative evidence. Eternal Gartua's summon candidates also share its level, so location/level OCR alone does not promise disambiguation.

## Gear requirements and modes

The public source explicitly supplies `instances.items[].modes.<mode>.itemLevel`. The six qualifying entries are:

- Vakron Sky Island: Explore 1400 and Conquest 1400.
- Ferocious Horn Den: Explore 2100 and Conquest 2100.
- Urugugu Canyon: Conquest 1400.
- Fire Temple: Conquest 2100.

Most other public instances omit item-level requirements. Their NPC level, star ordinal or database order does not establish GS.

The independent Steam map schema supplies `maps.records.<mapID>.entrance.EquipItemLevel`. The registry includes positive integer values >= 1400 only when the source explicitly uses a `Dungeon/` base directory. It excludes the 3000-GS Chaotic Middle Reshanta map because its source path is an interserver Abyss world map. Map type alone does not establish an instance.

Static Easy/Normal/Hard and other internal map variants remain raw source names. They are not converted into public Explore/Conquest variants. A profile can therefore retain a public Explore requirement of 700 while also having a separately sourced Hard-map requirement of 2400. Those describe different source contexts and do not justify overwriting the public requirement.

`required_gear_score` is populated only from an explicit single public mode linked by its actual boss key; otherwise it stays null. `minimum_target_gear_score` is the lowest known qualifying target requirement. Full `public_gear_requirements` and `gear_requirements` preserve the original fields and JSON pointers. Neither field measures a player's gear.

All 83 qualifying maps join a dungeon record through raw `MapId`, even when the dictionary's dungeon ID differs from the map ID. Of these, 77 have event records. Six Abyss Corridor variants have neither event entries nor identified named boss templates in this snapshot. Six unnamed Hall of Illusion Invisible entities have Monster/Hero classification but no English identity; they remain explicit diagnostics rather than fabricated boss names.

## Files, API and provenance

`research/scripts/build_sentinel_target_registry.py` verifies the complete 16-file supplied Steam manifest and decoded map/NPC/name/dungeon hashes. It persists the full reviewed public `bosses.json`, `instances.json`, `mechanics.json`, `LICENSE` and `provenance.json` under:

`research/boss-sources/skeeve/pins/25b6d5d1a62fededfbdbe67ab71c687f3820d8fb/`

The cached public files retain exact downloaded bytes, SHA-256 and Git blob hashes. A changed cache fails integrity checks; it is not silently relabeled as the reviewed commit. Source: [public boss catalog](https://github.com/SkeeveAN/Aion-DPS-Meter/blob/25b6d5d1a62fededfbdbe67ab71c687f3820d8fb/Backend/src/data/aion2/bosses.json), [public instance requirements](https://github.com/SkeeveAN/Aion-DPS-Meter/blob/25b6d5d1a62fededfbdbe67ab71c687f3820d8fb/Backend/src/data/aion2/instances.json), MIT license retained in the registry and cache.

The generated `aion_sentinel/assets/encounter_targets.json` contains all 1,002 existing profile keys, target flags, public boss keys, exact NPC IDs, map ownership, entrance requirements, dungeon joins, current warning counts and source conflicts. NPC/skill or map facts are not copied from a contradictory numeric ID merely because a public catalog lists it.

Runtime helpers in `target_registry.py`:

- `load_target_registry()` loads the bundled offline data.
- `profile_target(key)` returns an independent profile row or null for an unknown key.
- `target_profiles(category='all' | 'worldboss' | 'high_gs')` lists independent target rows.
- `target_summary()` returns source-bounded coverage counts.
- `apply_target_registry(library)` annotates an independent library copy, classifies existing world profiles and preserves identities, maps, mechanics and rank variants.

Rebuild with `python research/scripts/build_sentinel_target_registry.py`. These facts establish coverage of the reviewed identity lists. Complete live boss-warning coverage still needs actual visible cues or a verified encounter-event producer, measured timing evidence and later testing.
