# Static metadata compatibility audit

The standalone audit compares explicitly supplied English Steam JSON data with
the decoded SHA-256 pins retained in Sentinel's static reference assets. It
reports domain changes and explicit profile dependencies for review. A source
change does not establish a changed runtime mechanic, and a matching source
does not establish live EU compatibility. The audit never edits settings,
rules, reference assets, signatures or profile eligibility.

`aion_sentinel/data_compatibility.py` provides the standard-library-only
`audit_compatibility(reference_paths, domain_paths, *, baseline_paths=None,
header_paths=None, manifest_path=None, client_build=None, source_build=None,
max_profiles=200, max_ids=100)` API. The returned object is JSON-serializable.
`scripts/audit_encounter_compatibility.py` loads this one independent source
file by path; it does not import `aion_sentinel.__init__`, the UI or the app.
Neither entry point discovers installations, opens processes, reads binaries,
decompresses packs, starts capture, downloads data or runs tests.

## Explicit JSON inputs

- Repeat `--reference` for pinned format-1 assets with `language=en` and
  `region=steam`, such as `game_data_reference.json`, `boss_warning_reference.json`,
  `encounter_targets.json` and `skill_timing_reference.json`. The source hash
  layouts used by these assets are supported, including `sources.static`,
  `sources.steam` and `decoded_sha256` / `unpacked_sha256` field variants.
- Repeat `--domain DOMAIN=JSON_PATH` for independently decoded JSON documents.
  Each must declare the configured domain, schema version 1, an English
  `source.locale` and a `records` object. Exact file bytes are hashed; rewriting
  whitespace or source/cache metadata can change that hash.
- Repeat `--baseline DOMAIN=JSON_PATH` to supply the original decoded bytes.
  A baseline must match one unambiguous pinned decoded hash before its records
  can be compared. This distinguishes metadata-only changes from added,
  removed or modified record IDs. No unverified baseline becomes a source pin.
- Optional `--manifest` accepts the existing Steam manifest JSON contract.
  Optional `--header DOMAIN=JSON_PATH` accepts a JSON record with `domain`,
  `header.unpacked_sha256` and optional `packed_sha256`. These are declarations
  compared with the pins, not independent verification of pack contents. The
  A2DP header's decoded digest must not be confused with the packed file hash.
- `--client-build` and `--source-build` retain declared build identities. Equal
  decimal Steam build IDs still leave runtime compatibility unverified. The manifest's
  `game_version` remains opaque; no hash-to-Steam-build mapping is invented.

All input paths must name JSON files. JSON values with duplicate object keys
or non-finite numbers are rejected. Each file is bounded to 128 MiB. Output
contains hashes, IDs and diagnostics; it does not copy source records or
localization text into the report.

## Report interpretation

Each domain reports `matched`, `changed`, `missing`, `invalid` or `unknown`.
`comparison_basis` distinguishes exact decoded bytes from record equality
against a verified baseline. A byte change with equal baseline records reports
`status=matched`, `byte_status=changed`. A baseline/header error remains visible
in `errors`; it does not turn a failed auxiliary comparison into live approval.
Conflicting pins remain explicit and never select a hash by source order.
Missing inputs are missing observations, not proof that game data is absent.

Per-profile dependencies use explicit NPC, active-skill, map, dungeon-record
and range-record IDs retained in the references. `names` dependencies use
category/ID keys such as `npc/2300471`. A verified record comparison can report
`changed_explicit_record_id`; otherwise the audit reports only
`potential_domain_dependency`. Counts remain complete when output ID/profile
lists are truncated. Dependencies do not prove an executed cast, phase or
rotation, and cannot discover owners not present in the supplied references.

The report also retains missing execution-value domains: SkillEffectGroup,
SkillEffect, Abnormal, AbnormalEffect, SkillAbnormal, ServerBroadcastData,
Message, NpcPhase and BehaviourTree. Supplying a value domain marks it
`values_supplied_unbound`; it never creates ownership links or warning rules.
Localized buff names and SDK schemas alone do not fill these value tables.

The references themselves are explicit local trust inputs. Their raw SHA-256
is recorded, but this component does not verify their release RSA manifest.
The `policy` block always states that gameplay validation and automatic
profile disabling are absent. Callers should surface review diagnostics while
preserving existing known profile behavior.

## Usage

Run from the repository root with paths to separately prepared decoded JSON:

```powershell
python scripts/audit_encounter_compatibility.py --reference aion_sentinel/assets/boss_warning_reference.json --reference aion_sentinel/assets/skill_timing_reference.json --domain skills=research/decoded-current/skills.json --baseline skills=research/decoded-pinned/skills.json --client-build 25719316 --source-build 25719316 --output compatibility-report.json
```

The command emits its own JSON report to standard output and optionally creates
the explicitly named output file. Existing output files are never overwritten.
Exit code 0 means the audit completed, including reports with changed, missing
or invalid domain inputs; exit code 2 means a fatal reference/configuration/output error. Status is read
from the report, not inferred from the exit code. `--help` displays normal CLI
help. This example does not assert that its illustrative decoded paths exist.

Implementation verification was limited to source inspection and Python AST
parsing. No application, audit entry point, unit, integration, OCR or live-game
execution was performed for this change.

## Commander access

Use **Advanced → Compare decoded GameData** to select a current decoded JSON
and its domain. The Commander compares it with the shipped pins, shows a
read-only report and offers JSON export. Missing domains are reported because
a single selected domain is not a whole-build check. Verified baseline comparison
remains available through the standalone source CLI. No capture or rules are changed.
