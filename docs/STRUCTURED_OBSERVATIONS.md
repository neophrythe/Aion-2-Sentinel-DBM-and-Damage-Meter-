# Structured encounter observations — Sentinel 0.6.10 Unfinished Beta

AION Sentinel can replay and follow normalized, read-only boss observations alongside its existing OCR mode. The design borrows only the useful *data categories* identified in the local Legion Commander / dxgi.dll static review: actor name and template ID, map ID, boss HP, casting skill ID, and telegraph kind/geometry. The implementation and interchange schema are original Sentinel code. No vendor binary, IPC protocol, license mechanism or packet capture is required by this feature.

## Input format

The replay importer accepts one JSON object per line with a strictly increasing numeric `timestamp` and a `structured` object. For example, these are **synthetic test values, not verified AION 2 IDs**:

```jsonl
{"timestamp":1.0,"structured":{"source":"local_replay","state":"active","confidence":0.99,"boss_name":"Transcendent Bakarma","boss_template_id":12345,"map_id":678}}
{"timestamp":1.2,"structured":{"source":"local_replay","state":"active","confidence":0.99,"boss_name":"Transcendent Bakarma","hp_percent":82.4}}
{"timestamp":1.4,"structured":{"source":"local_replay","state":"active","confidence":0.99,"boss_name":"Transcendent Bakarma","casting_skill_id":84721,"telegraphs":[{"kind":"pressure_wave","confidence":0.99,"position":[12.0,24.0],"radius":4.0}]}}
```

`source` is a lowercase provenance label. `state` is `active` or `invalidated`. An invalidated observation clears the encounter and its timers. `confidence` must be 0–1; the configured Sentinel confidence threshold applies to the whole observation and to each telegraph. `boss_template_id` and `map_id` are retained as evidence but do not select a module, because the current catalog has collisions and no verified EU map mapping. `position` and `radius` are retained for review, but no player-relative jump call is inferred from them.

To create a replay in the portable app, choose **Recordings → Import structured JSONL** and select the file. Sentinel validates it, saves an `observations.jsonl` session and immediately opens replay using the current cue settings. To do the same from the source workspace, save the JSONL as `raw.jsonl`, then run:

```powershell
python -m aion_sentinel.importer raw.jsonl observations.jsonl
```

Use `--settings path/to/settings.json` to import with a specific validated Sentinel configuration. In Sentinel, open **Recordings → Replay observation log** and select `observations.jsonl`. The importer keeps the previous output intact if validation fails. The imported file is a local replay, not a live data source.

## Local live feed

Create an empty `.jsonl` file, then select **Start data feed** in the main window and choose that file. Sentinel follows only lines appended *after* it starts. An external read-only observer must append one complete JSON object per line, flush each line, and timestamp it with Python `time.perf_counter()` on the same Windows machine. The default maximum age is 2.5 seconds; send at least one fresh observation per second to keep encounter state current. The producer should emit `state: "invalidated"` when its map/session changes or it loses reliable state. Sentinel also clears the encounter when the file disappears, is replaced/truncated, or stops producing fresh observations for the configured maximum age.

The feed is selected separately from OCR capture. It records its own `structured_live` session, which can be replayed later. The optional command-line equivalent is:

```powershell
./dist/AION-Sentinel/AION-Sentinel.exe --structured-feed ./your-feed.jsonl
```

The feed tail rejects incomplete, malformed, stale, future and out-of-order lines. Existing file content is skipped at startup, so a previous fight cannot be replayed as live combat. The visible Live journal shows boss, HP, cast ID, telegraph kinds and invalidations. **A local data supplier using this schema is still required**; the app does not read the game or third-party DLL through this feed by itself.

Each mechanic in **Cues** now has `Verified cast IDs` and `Verified telegraph kinds` fields. Enter decimal IDs or lowercase kinds separated by semicolons, enable that mechanic, and save. A cast ID matches exactly; a telegraph kind matches exactly. Empty fields never trigger structured warnings. Boss identity still needs two fresh confirmations unless manual arming is selected; HP thresholds still need two consistent readings and a downward crossing. Existing cooldown, phase and timer rules apply. Cast and telegraph alerts identify their source in the log.

## Measured cast remainder and progress

An active structured observation may include `casting_remaining_seconds` in the finite range 0–600, or `casting_progress` in the finite range 0–1. Both require `casting_skill_id` in the same observation. The number must be a measurement of the currently running cast. A static casting/cooldown field or a damage-hit ID supplies no cast clock.

The engine associates the supplied skill ID with exact reviewed NPC ownership and an enabled in-scope timing rule. It checks the fresh stream against the same confidence and identity guards as other warnings. Decreasing remaining seconds can establish an estimated end time after consistent samples. Fraction-only progress needs several changing samples and a stable measured slope before a duration is estimated. Joining mid-cast is supported from the observed measurement. No first-seen name/ID is treated as the cast start.

For schema illustration only, these IDs are synthetic:

```jsonl
{"timestamp":1.6,"structured":{"source":"local_replay","state":"active","confidence":0.99,"boss_name":"Transcendent Bakarma","casting_skill_id":84721,"casting_remaining_seconds":3.2}}
{"timestamp":1.8,"structured":{"source":"local_replay","state":"active","confidence":0.99,"boss_name":"Transcendent Bakarma","casting_skill_id":84721,"casting_remaining_seconds":3.0}}
```

These example rows do not establish a real skill association and should not become a boss rule. When a real measured cast finishes, a zero remaining time with its identified active cast can clear that cast estimate. A missing measurement is left absent; an estimate expires after 2.5 seconds without fresh timing. Producer invalidation clears the encounter. Cast-end estimates and heads-up messages remain distinct from individual wave impacts and recurring schedules. See [cast timing](CAST_TIMING.md).

## Screen timing in observation journals

Automatic screen observation records accepted timing in a separate top-level `cast_timing` object in its ordinary `observations.jsonl` journal. This is not an additional field accepted by the two-field structured replay importer. Journals created by Sentinel can retain and replay it directly.

A screen record has `source` (`screen_remaining` or `screen_progress`), `state` (`active` or `idle`), `confidence` (0–1), `captured_at` equal to the surrounding observation timestamp and the boolean `independent_sample`. An active record requires `skill_name` plus `remaining_seconds` for `screen_remaining`, or `progress` for `screen_progress`. The same measurement bounds apply. An idle record omits the skill and both measurement fields. When no accepted evidence exists, the object is omitted rather than emitted empty.

The capture worker confirms independent, temporally consistent target-crop samples before recording timing. OCR-cache reuse, identical images and unchanged measurements cannot refresh it. The engine validates the stream again; malformed optional timing clears cast state while normal frame processing continues. Screen names must identify one owned skill or a complete owned candidate group belonging to a single warning rule; hidden or unsupported HUD evidence can prevent a countdown. Static `CastingTime` and cooldown units remain unproved.

## Measuring repeat intervals

After recording real attempts, choose **Recordings → Analyze measured cast intervals** and select the session's `observations.jsonl`. Save the resulting `timing-report.json`. The report counts cast and telegraph *onsets* and lists observed intervals within each attempt, plus median/minimum/maximum. It does not bridge resets, boss changes or long observation gaps. The same report is available from the source workspace:

```powershell
python -m aion_sentinel.timing observations.jsonl --output timing-report.json
```

These are measurements, not predictive warnings. Keep a repeat timer disabled until several EU attempts support a stable interval and the corresponding cue is verified.

## Evidence needed before gameplay claims

No cast IDs, telegraph labels, actor/template-to-encounter mappings, wave lead times or phase timings in the static review were validated against the EU/International English AION 2 client. The numeric example above must not be used as a real boss rule. The file follower exists, but an external observer that produces verified EU structured game data is still required. Foreground OCR, conservatively measured visible target casts and manually taught visual cues remain the directly available screen inputs. The 0.6.10 integration has no new application or live-game validation.

For Bakarma specifically, a generic `pressure_wave` telegraph does not establish the instant when a player should jump. That requires measured player-relative wave position and action latency; Sentinel therefore keeps the immediate “Jump now” candidate disabled.

## Phase context and recurrence preparation

An active observation may include `phase_key`, a nonempty phase identifier of at most 160 characters with no control characters. The field must reflect independently established phase evidence; a warning label or HP partition alone is insufficient. This schema support does not verify a supplier or authorize its observations as live training evidence.

The preparatory recurrence model remains inactive in the current UI. Screen observation lacks confirmed phase identity, while a generic local JSONL feed remains an unknown origin for training. A future verified provider must supply both fresh measured casts and confirmed phase context before learning can qualify completed attempts.
