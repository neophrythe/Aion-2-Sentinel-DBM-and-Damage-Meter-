# AION Sentinel — user guide

Version 0.6.10, Unfinished Beta. Windows 10/11, PC, AION 2 EU / International, English game client. Screen-OCR encounter warnings and an optional integrated damage meter. The 1,002-profile inventory identifies 51 world-boss profiles and 86 profiles on qualifying >=1400-GS source instance maps. These are identity and source counts; they do not establish complete mechanic coverage. This preview has not undergone new application, functional, unit, integration, executable, OCR, UI or live tests. See [implemented scope and remaining gaps](RELEASE_0.6.10_BETA.md).

In **Setup**, choose world bosses alone, world bosses plus >=1400-GS instance references, catalog bosses plus world bosses, or the existing elite scopes. In **Boss library**, category filters and GS reference columns expose the static target evidence. **Encounter guide** shows published responses, their sources and inactive guide facts. GS means a documented source entrance requirement; it does not measure your character's equipment.

The default beginner window only exposes **Combat HUD**, **Start/Stop observation** and **Damage meter**. Everything below referring to Setup, Cues, Boss library, demos, replays or manual choices belongs to **Advanced → Expert controls**. No profile, region or difficulty selection is required in beginner mode. See [automatic quick start](BEGINNER_MODE.md).

The protected portable build contains native-compiled Sentinel code and checks its own critical files with an internal release manifest. It omits its readable implementation source and build internals. This raises reconstruction effort; it is not Windows Authenticode signing or complete protection against reverse engineering. Third-party notices and source access remain included, and Qt libraries remain replaceable. See [Native binary distribution](protected/BINARY_DISTRIBUTION.md), or `BINARY_DISTRIBUTION.md` in the portable folder.

## Start

Extract the complete 7z or ZIP archive, then double-click `Start-AION-Sentinel.cmd` in the portable application folder. It checks that `_internal` is present and reports early startup errors. You can also start `AION-Sentinel.exe` directly from that folder. Python, capture drivers, and an internet connection are not required for the packaged OCR path. Settings and sessions are saved in the application's `data` folder, so keep the application in a writable location.

From this source workspace, double-click `Start-AION-Sentinel.cmd`. It opens the packaged application and writes a startup report to `%TEMP%\AION-Sentinel-startup.txt` if the application exits early.

Click **Run OCR demo** to exercise real local OCR, boss acquisition, four warning cues, the overlay, and recording with generated English panels. The demo is marked DEMO and does not calibrate your game. Click **Stop** before setting up live observation.

Damage capture starts separately through the **Damage meter** checkbox in the control window header and is off each time Sentinel starts. **Stop observation** and F8 stop OCR while leaving capture running; the legacy **Stop** button in Expert controls stops both. If Npcap is absent, enabling the meter offers guided setup for its separate driver installation. **Run simulated meter demo**, in the **Damage meter** tab, previews the table and damage HUD without network capture or Npcap. Keep the bundled `meter` folder with the portable application.

## Combat HUD

The combat display uses three separate transparent frames: centered action warnings, compact **Upcoming** timer bars and larger **Imminent** bars. A timer moves to Imminent at 10 seconds remaining by default. Colors and original geometric icons distinguish waves (gold), stagger (blue), water hazards (teal), damage windows (green) and enrage (red). All countdowns are estimates, marked `~`; source HP hints have a smaller **UNVERIFIED HP REFERENCE** label. No idle card covers the game outside a recognized encounter.

Open **Setup → Combat HUD** to change HUD scale, timer opacity and the promotion threshold. **Preview HUD** shows simulated cues for 12 seconds. **Arrange HUD** temporarily unlocks all three frames so you can drag each one separately, then restores the previous lock setting. Dragging switches off automatic alignment; click **Save settings** to retain positions. **Reset HUD positions** restores game-window alignment. Keep **Lock overlay and let mouse clicks pass through** enabled during play. The top **Combat HUD** checkbox and F7 show/hide all three frames together.

Automatic target-cast measurement needs no extra beginner control. When an owned skill label associated with one eligible warning rule appears beneath the target header with explicit remaining seconds or a conservatively recognized changing cast bar, Sentinel can add a **cast (est.)** countdown. Safe same-name groups retain their candidate IDs; Sentinel does not guess one ID. It checks independent samples and never starts a clock from the first skill-name appearance. The countdown and cast-end heads-up remain estimates. Hidden or unsupported cast displays can leave them absent. See [cast timing](CAST_TIMING.md).

Warnings fade after roughly three seconds. Stopping, resetting, changing encounters or losing confirmed identity clears old warnings and bars. Up to two recent warnings and eight nearest estimates are displayed. The warning text remains the configured English message; the visual redesign does not establish new boss mechanics or exact timings. Borderless/windowed mode is required for this separate desktop overlay.

## Damage meter

Enable **Damage meter** in the control window header when you want live readings. If Npcap is already installed, Sentinel starts its bundled capture worker directly. If it is absent, Sentinel offers to download the fixed **Npcap 1.89** installer from [the official publisher](https://npcap.com/#download), after your consent, and opens its visible installer with the normal Windows elevation prompt. Choose **Set up Npcap** to continue or **Cancel** to leave capture off. Review the publisher's license and installation options yourself. Sentinel does not bundle the installer, perform a silent installation or accept its license automatically.

Cancelling setup, declining elevation or an installation failure leaves the meter off; screen OCR remains available. If setup requires a reboot, Sentinel leaves capture off and does not restart Windows. Reboot when convenient and enable the meter again. Otherwise, Sentinel rechecks the required capture components and retries the worker, which detects the game connection on an active adapter and waits for decoded combat records. If Npcap restricts capture to administrators, the meter reports a permissions error. **Start / Stop observation** controls screen OCR independently.

The **Damage meter** tab shows **Player**, **Class**, **DPS**, **Damage** and **Share**. The default view includes all captured actors and targets. Expert controls can select a target from captured runtime IDs or filter to a confirmed party. An uncertain roster leaves observed actors visible; static NPC catalog IDs cannot substitute for captured targets. Rows within a report use the same elapsed interval. Missing capture data is not a zero-damage result. Current-build EU protocol coverage and combat accuracy remain unverified.

Names arrive separately from damage. Starting capture after login can miss the earlier character record, leaving numeric player labels while damage is counted. When the meter shows **Names pending**, keep it enabled during an area change or login so it can receive fresh identity records. Explicit name records update the matching player-ID rows without resetting damage. A new or reused ID does not justify assigning your newly observed name to older unidentified rows. If those earlier rows remain, **Reset damage counter** is optional for a fresh counter after names arrive. Your own character label depends on the explicit local-character record; combat rank or a guessed class does not confirm it.

- **Show damage HUD** controls the separate damage overlay. It shows up to eight players ranked by DPS. Hiding it leaves capture running.
- Clear **Lock damage HUD / click-through** to drag the overlay; re-enable it for play. Scale, opacity and recenter controls adjust this HUD independently of the boss-warning HUD. Save its position and display options to retain them across encounter profiles.
- **Reset damage counter** clears the displayed counter and starts its interval from the next decoded hit.
- **Finish current run** freezes the run while capture remains enabled. Export your result, then reset to begin a new run.
- **Export displayed rows** saves the current rows as CSV. Export before disabling the meter: stopping clears the table and HUD.
- **Run simulated meter demo** replaces live capture with generated data labeled **SIMULATED DEMO**.

Disable the header's **Damage meter** switch to stop its worker. **Stop observation** and F8 stop only OCR; the legacy **Stop** button in Expert controls stops both OCR observation and damage capture. The meter hides stale or unavailable readings. F9 resets only the boss encounter, and F7 toggles the **Combat HUD**. Use the damage tab for damage-counter controls. See [Damage meter](DAMAGE_METER.md) for the complete setup and measurement details.

Local **History** retains up to 100 native reports within a 32 MiB budget. Each report has an ID and an explicit/manual or heuristic ending reason. Run and boss-attempt entries overlap and must not be summed. Names come from supplied metadata; numeric actor IDs never merge across runs. Synthetic demo reports remain visibly tagged and are excluded by the default history filter.

## Broadcast and player-debuff responses

Published guides supply 3 broadcast mechanics and 9 player-debuff mechanics, with 14 exact English labels across 10 encounter identities. Each response requires the matching boss and instance and two independent fresh complete-line observations in its own channel. Broadcast text, player-debuff labels and target-cast labels are separate observations. A missing, stale, cropped or ambiguous label leaves the response absent. Custom game layouts can require expert region calibration; these definitions do not establish coverage of every message or debuff.

## Set up the game

1. Run the English client in windowed or borderless mode.
2. Keep **Find name, level and location regions automatically** enabled in **Setup**. Sentinel identifies the foreground AION2 window and searches its standard top-center target heading and top-right minimap heading. It combines a separately displayed level with the name and handles fused OCR such as `14Heladrir`. Nameplates in the world and quest mentions are excluded from these searches. No name/location rectangles or monitor selection are required in automatic mode.
3. Optional: select **Cast / mechanic messages** around a visible English message if it appears outside the target cast area searched automatically. Keep combat chat and unrelated UI outside this region. Use tight crops for lower latency. Automatic cast timing keeps using the original small target-anchored cue crop; a separate mechanic crop does not supply its cast clock.
4. Optional: select **Boss HP** around a numeric percentage or `current / max` display if it appears outside the target health area. Examples: `75%`, `1,500 / 3,000`, `1.5M / 3M`. A graphical health bar without numbers is not read as HP. Keep unrelated percentages outside this crop.
5. Keep **Automatically select boss / elite encounter profiles** and **Use English location text** enabled. Two consistent readings confirm each identity. The observer narrows shared names by location before using the variant preference; an explicit Explore/Conquest label overrides that preference. Unresolved locations or variants pause warnings. Easy/Normal/Hard labels are not translated into Explore/Conquest.
6. Choose a module in **Encounter profile** or **Boss library → Use selected boss profile**. In **Cues**, replace candidate phrases with actual English text, set the phase/warning text and enable desired rules. Separate alternatives with semicolons. Save settings. Edits are retained separately for each boss.
7. Click **Start observation**. The name must be recognized twice before automatic rules are active. Identity-only observation is supported while you collect evidence. If no boss name is available, turn off automatic selection, select the profile yourself, and enable manual arming.

Bring the game to the foreground after starting observation, or use F8 while AION2 is already in front. Sentinel automatically follows the client window and resolution. If the game is minimized, hidden behind another foreground app, or missing a readable target/minimap heading, observation waits and clears old predictions. It never supplies the current location from a boss spawn table.

For a custom HUD, disable automatic region discovery, choose the game monitor and manually select tight **Target / boss name** and **Location / dungeon name** regions. Include the displayed level and exclude other nameplates. Optional visual cue regions still require manual teaching. Automatic HUD discovery has been checked on the saved 2560×1440 Heladrir/Crypt screenshot and resized derivatives; this does not establish coverage of every HUD layout or a live encounter.

Fresh settings load prepared Bakarma text cues and 859 generated exact English skill-name rules across 209 profiles. Generated rules require two fresh readings of a complete cue-region line. They report observed text; live EU visibility remains unverified. The separate timing reference covers 550 accepted skill IDs across 209 profiles. Its raw cast/cooldown values do not become clocks; observed explicit seconds or changing target cast progress can supply a cast-end estimate. Existing saved disabled choices remain disabled. **Warn on recognized boss skill text** in Setup controls generated skill-name warnings. Source HP rules are initially enabled as clearly labeled **Reference phase** hints, with their own switch. Boss/cue/HP previews and the log show what OCR reads. Stop observation before editing capture or rule settings; selecting a different module during live observation is supported and clears previous timers.

**Automatic encounter scope** controls whether only catalog bosses, hero/legend enemies, or elite/hero/legend enemies can select profiles. Normal enemies never receive automatic boss mechanics. Source rank comes from explicit `NpcType`/`NpcSubType` enums. Matching names with plausible normal variants remain blocked until location and, where available, level distinguish them. Static spawn maps do not reveal where you are. Missing subarea labels remain unknown. Special profiles without supported warning facts retain disabled custom-rule slots; exact skill-name matches do not establish measured fight timings.

Keep the displayed level inside the target crop when a name is shared with normal monsters or summons. For example the static reference includes Level-45 Transcendent Bakarma alongside same-name Level-35/43 summons; a bare name cannot distinguish them. A validated structured feed may instead supply `boss_template_id`. An explicit unknown map ID immediately invalidates the previous location. The variant dropdown is a preference; confirmed location/mode evidence takes precedence, and a compatible manually selected profile is retained.

The Live page shows the recognized boss/elite and location. A different target, new location or multiple names clears the previous predictions. Saved edits reload when the same encounter returns. Automatic HUD mode requires both readable headings. In manual-region mode with no location crop configured, unique boss names can still select profiles; shared names may require a manual instance choice. A configured but unreadable or unknown location keeps warnings paused.

Each module supports up to 128 rules. **Add mechanic** adds a disabled rule that you can name and configure. Set an HP threshold to zero to turn that trigger off. Text, image and HP triggers can be combined on the same rule. The match selector chooses phrase or complete-line matching; confirming observations can be set from one to five.

## Visual cues

For a stable icon, indicator, or graphic that has no useful text, select **Optional visual cue** in Setup. While that cue is visible, click **Teach current visual cue** on the corresponding warning in Cues. Enable that warning and save settings.

Templates are matched inside the calibrated visual region. Their appearance, UI scale, and camera context matter. A learned icon can indicate a wave preparation cue; it does not measure a moving wave's arrival at the player. The application does not issue an automatic precise “Jump now!” call.

## Overlay, voice, and keys

- Drag the overlay into position and save settings to keep that position. In Setup, **Lock overlay** makes mouse clicks pass through it.
- **F7** toggles the **Combat HUD**. **F8** starts or stops OCR observation independently of damage capture. **F9** resets only the boss encounter. If another application has claimed a key, use the equivalent buttons.
- Sound and English speech can be changed in Setup. Voice uses an available Windows English speech voice; the warning sound remains usable if speech is unavailable.
- Select a mechanic in **Manual calls** and click **Call selected mechanic** to warn independently of OCR.

The helper excludes its own windows from supported Windows screen capture to prevent OCR from reading its own warning text. It uses a desktop overlay; it does not insert UI into the game.

## Boss library

The **Boss library** tab contains the complete copied English reference: 119 boss/variant entries, 48 instance entries and 263 mechanics, plus the separately sourced Heladrir identity profile. Search by boss, dungeon, variant or mechanic. Select a row to inspect its NPC identifiers, phase/HP triggers and severity. **Export complete reference JSON** preserves all entries, including instance mechanics that have no named boss. The exported reference is separate from observation settings.

The public source contains 54 HP triggers and 209 phase triggers. All 54 HP thresholds occur in 23 modules and load as reference hints. Three additional reactor thresholds (90/60/30%) require confirmed map and template evidence. An HP hint needs two above-threshold readings, followed by two nonincreasing readings at/below the threshold; joining already below it does not fire. Wipe and avoidable-wipe responses receive higher warning priorities while retaining the reference label. Source phase entries without observable cues remain disabled. The public source supplies no fight-second repeat intervals or cast-start mapping. **Boss library → Export warning coverage** distinguishes skill-text rules, HP hints and unbound phases for all profiles. See [Boss warnings](BOSS_WARNINGS.md) for the complete evidence and limitations.

Some Bakarma variants share NPC identifiers. The current pinned mechanic correction assigns the three Draupnir source phase facts to Transcendent Bakarma; source phases without observable cues stay inactive. Prepared guide cues and owned English skill responses remain available. NPC identifiers are reference facts; the OCR app still requires confirmed English names and instance context.

## Timers and resets

Manually configured repeat intervals and estimated enrage default to zero (off). Set measured values in Cues after observing several attempts. A confirmed text, visual or HP trigger starts its configured repeat countdown. Estimated enrage starts from boss acquisition, which can be later than the actual pull. The combat HUD displays up to eight nearest estimates across Upcoming and Imminent; reminders are labeled **Estimated**. A countdown expires and does not restart without a new matching cue.

The separate local learner requires exact encounter, NPC/map, difficulty and explicitly confirmed phase identity. At least five intervals across three completed live attempts must remain within 15% variation before a recurrence estimate is eligible. Demos, replay, incomplete attempts and unknown phases do not qualify. Current screen observation leaves phase unknown, so these predictions wait for verified structured context. They estimate another observed onset and do not establish an attack sequence, wave impact or player-relative jump time.

Measured cast-end estimates are separate from those repeat timers. Keep automatic HUD discovery enabled; the target header must match the selected encounter, and the skill must have an unambiguous exact source association. Explicit neighboring seconds must decrease consistently. Fraction-only cast progress needs several changing measurements with a stable slope. In Expert **Cues**, **Cast-end heads-up** defaults to 3 seconds before the estimated end; set it to zero to disable that heads-up. The configured 5-second Bakarma range-warning reference does not automatically become this threshold or a wave countdown.

A frozen frame or unchanged measurement does not refresh a cast estimate. Fresh cast timing must continue within 2.5 seconds; expiry, confirmed idle evidence, focus/window changes, reset and stopping clear it. A plain graphical HP bar does not count as cast progress. Other bar appearances may also be outside the conservative detector. See [cast timing and source limits](CAST_TIMING.md).

HP transitions require two consistent readings. A single large misreading does not trigger a phase. Each HP rule fires once per encounter when confirmed health crosses its threshold downward. Joining below a threshold does not announce it retrospectively. Confirmed `0%` ends the encounter and clears timers; a subsequent confirmed high-health reading allows a new pull.

Resetting, changing boss/profile, stopping observation, or losing the recognized boss for eight seconds clears predictions. Losing capture data also lets that watchdog expire. Manual arming intentionally keeps the observer armed until you stop/reset it.

After a player death or wipe, press **F9** or **Reset encounter**. This release does not automatically detect player death.

## Record and replay

Every observation session saves a local `observations.jsonl` journal. It includes source timestamps, OCR text and confidence, visual scores, recognized warnings, processing latency and accepted screen cast-timing evidence. Enable **Save selected OCR crops** in Setup to retain image evidence. A session stops recording after its 250 MB budget while observation continues.

In **Recordings**, open the session folder or replay an `observations.jsonl` file. Replay uses original settings and timing, automatically follows recorded boss names, and handles manual profile changes, calls and resets. Replay sound is muted, and your live settings are restored afterward. No files are uploaded.

**Import structured JSONL** accepts normalized read-only boss observations for local replay. The Cues tab has optional verified cast-ID and telegraph-kind fields for each rule. An external structured producer is still required to supply verified EU cast IDs and telegraphs. It can also provide measured remaining cast seconds or progress with an identified cast; an ID alone supplies no countdown. See [Structured encounter observations](STRUCTURED_OBSERVATIONS.md) for the file format, validation and import procedure.

**Start data feed** follows new lines in a local normalized JSONL file while an external observer writes them. It records its own replayable session and clears predictions when data stops. **Analyze measured cast intervals** exports observed repeat intervals from a session. The feed format and timing-report limits are documented in the same structured-observation guide; Sentinel does not supply an AION 2 game-data producer.

Settings can be exported and imported in Setup. Imported visual images are not automatically copied; teach those cues on the new machine. Automatic HUD discovery follows the game client size; manually selected regions and taught visual cues may need recalibration after monitor, resolution or UI-scale changes.

## Troubleshooting

If no text appears, check the region previews, English language, text size, and whether the game is visible. For delayed OCR, reduce crop sizes or the requested sampling rate. Sampling frequency is an upper bound; inference is sequential and does not queue old frames. Stale results are rejected.

If a cue repeats incorrectly, tighten the crop and use a more specific phrase. The observer waits for a phrase to disappear before allowing another warning. Disable a misleading cue while refining it.

The last application error is saved as `data/last-error.txt`. The packaged model files are local. The Windows C++ runtime must be available. This 0.6.10 Unfinished Beta has not undergone new Windows application tests. A blank game capture is not evidence of an absent mechanic.

## Development

Use Python 3.11 or later in a project environment:

For portable builds, use a clean CPython installation. The build script excludes unrelated Conda and tool-runtime DLL directories from its child process search path and backs up existing portable app data before rebuilding.

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements-dev.txt
.\.venv\Scripts\python.exe -m aion_sentinel
.\.venv\Scripts\python.exe -m pytest -q
.\.venv\Scripts\python.exe -m aion_sentinel --self-test --output artifacts/ocr-test.json
.\.venv\Scripts\python.exe scripts/build_windows.py
```

The OCR helper and Qt controls are Sentinel code. The English boss reference derives factual fields from SkeeveTV's MIT-licensed Aion-DPS-Meter repository; its license and provenance are included. The optional integrated native meter adapts the pinned MIT-licensed Aion Companion capture, parser and combat-analysis sources. Maintainers retain Sentinel's adapted implementation source separately; the protected portable application includes dependency notices and covered third-party source availability. DBM source remains a separate research reference. See [Damage meter](DAMAGE_METER.md) for provenance and current measurement limits.
## Local boss GameData, version 0.3.0

The local English Steam reference is now available in **Boss library → View local GameData**. Select an NPC record to inspect its map name, difficulty label and linked English skills. Identical boss names can belong to different instances; the reference does not automatically choose an instance variant.

To prepare a skill-name warning, select the appropriate encounter profile, stop observation, open **Cues → Browse boss GameData skills**, select the skill and click **Add disabled OCR skill cue**. Review the new rule, observe whether its English text actually appears in your calibrated cue region, then enable and save it. The helper announces detected text; the reference alone cannot establish a cast start or mechanic phase.

Raw cast/cooldown, berserk and groggy settings remain reference facts. The timing display also exposes reviewed configured range-warning and wide-casting alert values. Raw `CastingTime` and cooldown units are unproved and supply no clock or repeat interval. For `Wave of Death`, `18000` casting and `1000` cooldown are raw values; `5000 ms` is a reviewed static range-warning lead, not a synchronized future wave.

All accepted generated skill IDs have a configured gauge/floater hiding flag, so names or bars may never appear on screen. Generated text rules need observed complete text; a separate cast countdown needs explicit remaining seconds or fresh changing cast progress under the confirmed target header. Hidden metadata creates no artificial bar. Missing measurements leave the countdown absent. Disable a misleading rule while refining the crop. Existing learned visual cues and manual warnings remain available. See [cast timing](CAST_TIMING.md).



Published mechanic references, approximate HP ranges and typed duration claims are available in the expert Boss Library under Encounter guide. They do not supply automatic phase or wave clocks. See [reference scope](ENCOUNTER_RESEARCH.md).
