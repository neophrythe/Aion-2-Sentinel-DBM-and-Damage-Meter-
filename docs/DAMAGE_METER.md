# AION Sentinel — integrated damage meter

Version 0.6.13 source implementation, Unfinished Beta. Windows x64, AION 2 EU / International, English interface. Current-game compatibility and gameplay validation remain pending.

The protected portable release includes the compiled native meter worker and native-compiled Sentinel UI. Its own critical files are checked against an internal RSA release manifest; this is not Windows Authenticode signing and cannot prevent all reverse engineering. The archive omits Sentinel's implementation source, while retaining third-party notices and covered-source access. See [Native binary distribution](protected/BINARY_DISTRIBUTION.md), or `BINARY_DISTRIBUTION.md` in the portable folder.

Sentinel includes its own bundled packet capture, protocol parser and damage-analysis worker. Enable it from Sentinel's control window; no separate meter application or account is needed. The worker observes game traffic passively and returns local snapshots to Sentinel's table and damage HUD. Boss warnings use screen OCR and configured encounter cues. Optional native NPC observations can supplement a visible target's identity, raw current HP and death status under the strict client-matching rules below.

Capture is **off at startup**. Npcap is a separately installed prerequisite for live capture. The screen-OCR observer and simulated meter demo work without it.

## 0.6.13 beginner mode — Unfinished Beta

The simplified control window uses a **Damage meter** switch. Enabling it starts Sentinel's bundled live worker and automatic adapter discovery. An adapter selector, character-name field and separate meter launcher are unnecessary. The worker probes active IP connections, including VPN interfaces, and accepts a connection only after decoding game evidence. Disabling the switch stops the worker, clears its rows and hides the damage HUD. Enabling it again starts a fresh counter.

Live capture requires a working Npcap installation and permission to open capture adapters. If Npcap is absent when you enable **Damage meter**, Sentinel offers guided setup for the fixed **Npcap 1.89** installer from [Npcap's publisher](https://npcap.com/#download). Choose **Set up Npcap** to consent to the download, or **Cancel** to leave capture off. Setup then opens the normal visible installer with Windows elevation. Review the publisher's license and installation options yourself. There is no silent installation or automatic license acceptance, and the installer is not bundled with Sentinel. An existing Npcap installation skips this helper; it can still have capture-permission problems.

Cancelling setup, declining Windows elevation or an installation failure keeps the meter off; screen OCR remains available. If installation reports that a reboot is required, Sentinel leaves capture off and does not restart Windows. Reboot when convenient, then enable **Damage meter** again. Otherwise, Sentinel rechecks the required capture components and retries its bundled worker. If capture access is denied or another prerequisite is missing, follow the status message and retry the switch after resolving it. Keep the meter enabled during login or an area change if player names are pending; decoding a damage record alone cannot supply a missing name record.

The default display automatically selects the current captured boss attempt, separating retries. A defeated attempt keeps its damage and DPS result until later damage starts another fight. A catalogued final boss's result remains visible when its completed run is cleared. Before a catalogued boss is captured, the automatic display uses counter totals. The separate **All targets · counter totals** view retains the independent counter since reset. Its damage is not changed by selecting another view. The backend closes a run on an observed dungeon/zone-label change, a catalogued final boss's confirmed death after its grace period, or ten minutes without accepted damage or fresh boss activity. These are observed or inferred boundaries rather than a complete game combat log.

Focused offline checks cover selection, first-to-last DPS timing, transport continuity, Deus recognition, tick parsing, nested compression and late summon attribution. They do not establish agreement with other meters in a current live encounter. The detailed controls below are available in Expert controls and are not required to start capture in beginner mode.

## Start and stop

1. Keep the complete portable folder together, including `meter/SentinelMeter.exe` and its accompanying assets and licenses.
2. Start Sentinel and enable **Damage meter** in the control window header. If Npcap is absent, accept the guided setup only if you want live capture; complete the visible Npcap 1.89 installer and its Windows elevation prompt. You can instead install Npcap yourself from [the official download page](https://npcap.com/#download).
3. If setup needs a reboot, restart Windows when convenient and enable the meter afterward. Otherwise, Sentinel rechecks capture components and retries the worker. An administrator-only Npcap installation can require administrative rights to open capture adapters. Open the **Damage meter** tab in Expert controls to see its source status.
4. Bring the game into a normal combat encounter. Sentinel detects a connection from decoded game evidence on an active adapter and waits for damage records. Player metadata may arrive after a login or area change.
5. Disable **Damage meter** to stop capture. Stopping clears the displayed rows and hides the damage HUD; export a result first if you want to keep it.

Damage capture and screen-OCR observation have separate controls. **Stop observation** and F8 stop OCR while leaving the meter running. The legacy **Stop** button in Expert controls stops both OCR observation and damage capture. F9 resets only the boss encounter. Closing Sentinel shuts down its owned meter worker.

## Table and measurements

The table displays **Player**, **Class**, **DPS**, **Damage** and **Share**, ranked by DPS. The summary shows the target label, elapsed time and totals for the displayed rows. When captured damage spans multiple targets, the counter can show **All targets**. A missing name uses a numeric label or an unidentified target.

All rows in a view use the same interval, from the earliest through the latest retained damage record for the selected scope and included actors. Each player's DPS is captured damage divided by **max(1 second, last hit minus first hit)**. The exported elapsed time is the actual span; `dps_divisor_seconds` separately records the one-second floor. Idle screen time does not lower DPS. If damage resumes after a mechanics pause, that intervening pause is included in the new first-to-last span. Manual finish and automatic completion follow the same measurement rule. Share is the displayed player's fraction of displayed damage. Different target scopes, filters, resets and intervals can produce different DPS without different damage totals. For example, 600,000 damage spanning twenty seconds stays at 30,000 DPS while the screen is idle; a later hit extends the interval.

Automatic boss mode counts that boss target only. Adds are included in **All targets · counter totals** instead. This differs from meters that include boss and adds in one encounter. Compare the same scope and interval before interpreting a difference.

The **Display** selector defaults to **Automatic · current boss attempt**. Choosing a known boss shows its latest attempt; a selected ordinary target falls back to its current-run totals. **All targets · counter totals** shows the independent counter. A counter reset selects that explicit view so the empty counter is visible; select Automatic again to return to boss attempts. Run, counter and attempt views overlap and should not be added together. The summary identifies the displayed scope and identifies the last-hit measurement clock.

**Confirmed party only** applies after the native worker has confirmed a party roster. Until that evidence exists, the requested filter falls back to all observed actors and the status says that the party filter is waiting. Captured targets appear with their runtime IDs; exact catalog matches can carry a boss label. Neither a party request nor a numeric target selection confirms complete capture coverage. A displayed class, local-player marker or summon attribution can remain incomplete; missing records do not establish zero damage.

Archived boss attempts and ordinarily closed runs end at the last retained hit. Damage received within the existing three-second death grace corrects the same attempt and its last-hit endpoint. Manual completion records its boundary time separately; displayed DPS and retained damage intervals still end at the last selected hit. Boss activity does not change these calculations, manufacture damage, or supply a separate DPS timer.

The damage HUD shows up to eight rows. The main table retains all rows in the current snapshot.

## Summons and damage ticks

Recognised summon attacks use minimal numeric compatibility classifications without a full skill-name catalog. If ownership is unresolved, an **Unassigned summon** row preserves accepted damage rather than silently discarding it. A confirmed unique-class party or own-character context can resolve ownership; ambiguous same-class parties remain unassigned. Explicit spawn/cast ownership remains supported. This fallback is observed-context inference, not an authoritative game ownership API.

Later ownership transfers provisional damage to the owner in current-run and counter aggregates, boss attempts and bounded retained current-run reports. It preserves total damage, skill amounts, direct hit/critical counts and time bins. Entity generations prevent reused IDs from transferring older contributions. A reset counter stays cleared; previous runs are not retrospectively merged.

Compact damage ticks are accepted with validated effect/skill identities. Ticks contribute damage without inventing direct hits or critical hits. Healing and known non-damage effects are excluded, including the published NPC self-heal format. Nested compressed packets are bounded by depth, expansion size and frame count. These cases do not establish complete current-build protocol coverage.

## When player names are pending

Damage and player names arrive in separate server records. Enabling capture after login can miss the earlier character record, so the meter may show damage beside a numeric label such as **Player 1234**. The tab and damage HUD show a names-pending hint while rows are unidentified.

Keep the meter enabled during an area change or login so it can receive fresh name and character records. In version 0.6.4, an explicit name record updates the matching player-ID rows without resetting their damage. The update can appear even when no further damage is dealt. Your own character label requires its explicit local-character record; the highest damage row or an inferred class does not identify you.

The meter uses observed IDs to match names. A new or reused ID does not justify assigning a newly observed name to unrelated older anonymous rows. Those rows can remain in the accumulated counter after an area change. Once the new names arrive, **Reset damage counter** is optional if you want a fresh named counter. Export the existing rows first if you want to keep them. Resetting is not required for a name update on the same confirmed ID.

Receiving a name confirms that record's label, not complete party membership, summon ownership or current-build damage accuracy. Missing records and unsupported protocol changes can still leave names unavailable.

## HUD and controls

- **Show damage HUD** shows or hides the separate damage overlay.
- **Lock damage HUD / click-through** lets mouse clicks pass through. Clear it to drag the HUD, then lock it again for play.
- **HUD scale**, **Opacity** and **Recenter damage HUD** adjust the damage overlay independently of the three boss-warning surfaces. Scale ranges from 65% to 180%; opacity ranges from 30% to 100%.
- Damage HUD position, visibility, lock, scale and opacity are retained through its independent settings. Capture remains off at the next launch.
- **Reset damage counter** clears only the independent HUD counter and returns the selector to all targets. Its next interval begins with the next decoded hit. The current run, boss attempts and saved history remain available. After a manually finished run, reset starts a new run while preserving captured metadata.
- **Finish current run** freezes the current run and stops adding damage to it. Capture remains enabled. Export the result, then reset to measure another run.
- **Export displayed rows** saves a UTF-8 CSV with player name, actor ID, class, DPS, damage, share, local-player marker, elapsed seconds, target, source label, run/report IDs and boundary fields where available. It exports the displayed player rows, rather than the report's skill and timeline data. A CSV is not a replay or complete combat log.
- **Export meter comparison** saves a JSON snapshot of the displayed damage, DPS, hit/crit counters, measurement interval, clock policy, scope, filters and capture counters. Compare the same player's damage and the same fight interval across meters. The export contains player labels but no raw traffic, account credentials or API tokens.
- **History** opens locally saved run totals and boss attempts. A selected report can be exported separately.
- **Run simulated meter demo** replaces live capture with generated players and damage records. The table and HUD label this **SIMULATED DEMO**. Npcap and a running game are unnecessary for the demo.

F7 and the **Combat HUD** checkbox control the three boss-warning surfaces. Use **Show damage HUD** for the damage overlay.

## Boss attempts and local history

A catalogued boss attempt begins from accepted damage, not from a nearby NPC spawn or an HP reading. Confirmed HP-zero or kill evidence closes it as defeated. In the absence of that evidence, 45 seconds without damage or accepted fresh boss HP activity closes it with an inferred **Combat idle** boundary. Fresh positive-HP observations can keep an already open attempt during a mechanics phase; a stale, repeated, out-of-order or future timestamp cannot extend it or bridge a gap that already expired. Capture silence remains unknown and cannot prove victory.

The HUD counter, current-run target view, full run report and individual boss-attempt reports can contain the same hits. Their different IDs and view labels preserve their scope; do not total them together. A live display filter does not filter saved history: completed reports retain all observed actors.

History keeps up to **100 reports / 32 MiB** locally, with a 16 MiB limit for an individual stored report. Same-report corrections update that report rather than merging numeric actor IDs across unrelated runs. The saved report data includes per-player skill damage, hits and critical hits, plus a bounded one-second damage timeline. The native timeline has a three-hour span and 120,000-bucket ceiling; a truncated timeline is marked. The current History dialog lists reports and player rows and shows the timeline-point count. It does not present a skill table or timeline chart. If disk persistence fails, the status explains that reports remain available for the session.

## Optional native encounter evidence

The passive bridge buffers fresh native NPC identity and HP/lifecycle observations. It supplements a target only after repeated independent observations, an exact supported NPC/name match to freshly read target OCR, and agreement between the captured foreground game-window PID and the authoritative Windows TCP socket-owner PID. A nearby spawn, an absent process identity, or a similar name is insufficient. Ambiguous matches remain unlinked diagnostics.

The Live display can show the matched actor/NPC IDs, raw current HP, and observed death. Raw HP has its own freshness limit of 2.5 seconds; later identity updates do not refresh an old HP measurement. A confirmed death is preserved within the native scope until newer positive-HP evidence or a scope change. Scope resets, capture restarts, client mismatches and focus/layout changes clear target bindings. Recorded native observations are replayed within the recording's own scope and clock; current live capture is excluded from replay.

This evidence supplies no authoritative maximum HP, HP percentage, phase identity, cast-start timing or complete boss coverage. Boss activity changes only idle-boundary evidence; the shared DPS denominator still comes from retained damage timestamps and the snapshot/report endpoint described above. Existing OCR cues and independently confirmed context remain necessary for mechanic warnings.

## Source status and limits

The status line reports capture state, received packet count and decoded damage-record count. Readings are hidden when the source is unavailable, fails validation or stops providing fresh snapshots for more than three seconds. Check the status before interpreting an empty table.

The parser's pinned reference and annotated fixtures describe **EU early access, 30 September 2026, TCP port 13328**. This is upstream calibration evidence. Current EU build compatibility, complete combat coverage and damage accuracy have not been validated in a live encounter. A game update can change the protocol while screen OCR continues working.

Player names, classes, local-player identity, party membership and summon ownership depend on available decoded metadata. PvP and complete healing or defense analysis are outside the current meter's supported display. The 0.6.11 source adds a local exact-NPC boss catalog derived from Sentinel's existing reference data and retains compatibility skill-name data. Unlisted, unavailable or undecoded IDs can still use numeric labels; an unlisted NPC is unclassified, not proof of an ordinary mob. Static catalog labels and dungeon associations do not verify current-build protocol coverage or every encounter variant.

If Npcap is missing, enabling **Damage meter** offers guided setup. If you cancel, setup fails, capture access is denied or a reboot is required, readings remain off and the status explains the next step. Resolve the reported prerequisite or permission issue, then re-enable **Damage meter**. If the bundled backend is missing, re-extract the complete Sentinel folder. The simulated demo previews the table, HUD and controls independently of live capture; it does not validate current-game traffic.

## Source provenance and notices

Sentinel adapts MIT-licensed source from [xzHannes/aion-companion](https://github.com/xzHannes/aion-companion) at commit `dbc3c275fe1846c8a98b531b966d227cb4d0ca02`. Its attributed parser subset originates from SkeeveAN/Aion-DPS-Meter at `ea8fca7e0b629a46da8ce8560462f52e05a0ffeb`. Sentinel's local worker entry point and snapshot interface are adaptations around those sources, retained in the maintainers' project.

The protected portable release includes provenance in `meter/NATIVE_NOTICE.md` and licenses under `meter/licenses`; it does not include Sentinel's adapted implementation source. SharpPcap 6.3.0 uses MIT. Unmodified PacketDotNet 1.4.7 uses MPL-2.0 and is compiled into the NativeAOT worker; its covered source remains available through `meter/licenses/dependencies/PacketDotNet-1.4.7/SENTINEL-SOURCE-AVAILABILITY.md`. Npcap is supplied separately by its publisher. LGPL Qt/PySide6 source and replacement instructions are under `licenses/Qt/`.
