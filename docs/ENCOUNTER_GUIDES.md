# Published encounter responses

Research date: 10 October 2026. This reference adds English instructions to
an already observed skill cue. It does not establish a complete encounter
timeline or claim that those instructions have been tested against the EU game.

Files:

- `aion_sentinel/assets/encounter_guide_reference.json`: sources, 35 encounter
  entries, 83 concise mechanic references, 19 exact skill-response candidates,
  five named Abyss identity references and explicit coverage gaps.
- `aion_sentinel/encounter_guides.py`: exact encounter/skill advice lookup.
- `research/scripts/build_sentinel_encounter_guides.py`: reproducible serializer
  for the manually researched facts, with structural checks only.

## Integration

Call `published_skill_advice(boss_library_entry, skill_name, reference=None)`.
The boss entry must contain `name` and `instance_name`. The result carries
`action`, `label`, `mechanic_ids`, `source_urls`, `scope`, `evidence`,
`live_verified=False`, `requires_local_owned_skill_join=True` and
`minimum_distinct_ocr_samples=2`. A missing, conflicting or ineligible response
returns `None`.

The caller must establish all of the following before using that response:

1. The selected profile identifies this exact boss and instance. A boss name
   alone is insufficient; the same name can occur in different encounters.
2. The local English client data explicitly lists the observed skill in that
   NPC's owned skill list. Nearby numeric skill IDs, translated names, shared
   animations and generic buff names do not prove ownership.
3. The existing observed-cast rule confirms the complete skill label on two
   distinct OCR samples. Guide lookup enriches that rule's instruction; it does
   not create a new cast, detect a phase or predict a later event.

Explore/Exploration/Conquest catalog display suffixes are stripped for the
instance lookup. Hard, Normal and other mode names are not translated into
those variants. Returned advice must retain its source URL and unverified
status. A status count of eligible guide candidates is not a count of live
working warnings.

`guide_for_profile()` returns the exact linked guide for display.
`guide_coverage()` describes the static reference inventory and gaps.
`load_encounter_guides()` loads the packaged JSON and rejects malformed data.

## Source scope

The 14 Global reference encounter entries come from the original maintainer
[Aion 2 Maps](https://aion2maps.com/guides/vakron-sky-island/), whose guides cite
Global Steam build 25650019, Taiwan comparison data and creator observations.
That provenance establishes published references, not this application's own
EU combat validation. Exact reported skill names can become warning responses
only after the local NPC ownership check described above.

The remaining guides carry their Korean/Taiwan reference scope or historical
early-access scope. Their visual instructions, broadcasts, debuffs and objects
remain available as source annotations; the exact-skill helper excludes them
from current Global automatic enrichment. Five working source-name entries
are deliberately unlinked where the local catalog uses different spellings.

[Azure Breath Island](https://aion2codex.com/entry/d8d6233c-616e-4afa-91da-b402f0c14600/azure-breath-island-boss-dungeon-guide-d8d6233c)
explicitly limits its older footage and English lookup names. The
[Cradle of Nihility source](https://aion2t.com/guides/cradle-of-nihility) is a
February reference guide. Neither establishes present EU mode behavior.

[NCSOFT's 5 October notice](https://lounge.plaync.com/feed/83063?country=US&locale=en-US)
temporarily removed the Global Sanctuary raid pending adjusted mechanics.
Every [early-access Ludra response](https://aion2maps.com/guides/ludra/) is
therefore excluded from automatic current-Global advice until newer encounter
rules establish it again.

## Thresholds, timing and missing coverage

All HP percentages in this asset are disabled source-reference hints.
Approximate or conflicting ranges are never reduced to one active threshold.
The one exact historical source claim still does not establish a Global phase
trigger. No cast duration, repeat interval, ring arrival or enrage countdown is
created from these guides.

The researched [world-boss source](https://aion2guidance.com/en/bosses/) and
[Abyss guide](https://aion2maps.com/guides/abyss/) provide identities and content
or spawn references. They do not establish exhaustive English mechanic
responses for every world boss. Those gaps remain explicit; the separate local
NPC-owned skill reference can still support generic observed attack warnings.
Public DPS meters, spawn timers and translated companion guides are recorded
as tools with their actual scope, without claiming a DBM mechanic timing pack.

No unit, integration, OCR or live-game functional tests were executed for this
change. Only source research, JSON serialization and Python AST/JSON parsing
were performed, as requested.
