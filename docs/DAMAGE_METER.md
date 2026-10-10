# AION Sentinel — integrated damage meter

Created by **Neophrythe & Dr.Tatsu**.

Version 0.6.7, Unfinished Beta. Windows x64, AION 2 EU / International, English interface.

The protected portable release includes the compiled native meter worker and native-compiled Sentinel UI. Its own critical files are checked against an internal RSA release manifest; this is not Windows Authenticode signing and cannot prevent all reverse engineering. The archive omits Sentinel's implementation source, while retaining third-party notices and covered-source access. See [Native binary distribution](protected/BINARY_DISTRIBUTION.md), or `BINARY_DISTRIBUTION.md` in the portable folder.

Sentinel includes its own bundled packet capture, protocol parser and damage-analysis worker. Enable it from Sentinel's control window; no separate meter application or account is needed. The worker observes game traffic passively and returns local snapshots to Sentinel's table and damage HUD. Boss warnings continue to use screen OCR and your configured encounter cues.

Capture is **off at startup**. Npcap is a separately installed prerequisite for live capture. The screen-OCR observer and simulated meter demo work without it.

## 0.6.7 beginner mode — Unfinished Beta

The simplified control window uses a **Damage meter** switch. Enabling it starts Sentinel's bundled live worker and automatic adapter discovery. An adapter selector, character-name field and separate meter launcher are unnecessary. The worker probes active IP connections, including VPN interfaces, and accepts a connection only after decoding game evidence. Disabling the switch stops the worker, clears its rows and hides the damage HUD. Enabling it again starts a fresh counter.

Live capture requires a working Npcap installation and permission to open capture adapters. If Npcap is absent when you enable **Damage meter**, Sentinel offers guided setup for the fixed **Npcap 1.89** installer from [Npcap's publisher](https://npcap.com/#download). Choose **Set up Npcap** to consent to the download, or **Cancel** to leave capture off. Setup then opens the normal visible installer with Windows elevation. Review the publisher's license and installation options yourself. There is no silent installation or automatic license acceptance, and the installer is not bundled with Sentinel. An existing Npcap installation skips this helper; it can still have capture-permission problems.

Cancelling setup, declining Windows elevation or an installation failure keeps the meter off; screen OCR remains available. If installation reports that a reboot is required, Sentinel leaves capture off and does not restart Windows. Reboot when convenient, then enable **Damage meter** again. Otherwise, Sentinel rechecks the required capture components and retries its bundled worker. If capture access is denied or another prerequisite is missing, follow the status message and retry the switch after resolving it. Keep the meter enabled during login or an area change if player names are pending; decoding a damage record alone cannot supply a missing name record.

The default measurement includes all captured actors and targets. It is a cumulative counter for the current run, with a shared elapsed-time denominator. An ordinary boss death does not automatically reset it. The backend closes and clears a run on an observed dungeon/zone-label change, a catalogued final boss's confirmed death after its grace period, or ten minutes without damage. Those boundaries depend on decoded evidence and are not a guarantee of one isolated counter per boss. Switch the meter off and on to explicitly begin a fresh measurement; this also discards earlier captured identity metadata.

These statements describe the source implementation. The 0.6.7 guided setup, beginner control path, automatic adapter selection and current-game capture have not undergone new application, functional, unit, integration or live tests. The advanced controls described below belong to the detailed interface and are not required to start capture in beginner mode.

## Start and stop

1. Keep the complete portable folder together, including `meter/SentinelMeter.exe` and its accompanying assets and licenses.
2. Start Sentinel and enable **Damage meter** in the control window header. If Npcap is absent, accept the guided setup only if you want live capture; complete the visible Npcap 1.89 installer and its Windows elevation prompt. You can instead install Npcap yourself from [the official download page](https://npcap.com/#download).
3. If setup needs a reboot, restart Windows when convenient and enable the meter afterward. Otherwise, Sentinel rechecks capture components and retries the worker. An administrator-only Npcap installation can require administrative rights to open capture adapters. Open the **Damage meter** tab in Expert controls to see its source status.
4. Bring the game into a normal combat encounter. Sentinel detects a connection from decoded game evidence on an active adapter and waits for damage records. Player metadata may arrive after a login or area change.
5. Disable **Damage meter** to stop capture. Stopping clears the displayed rows and hides the damage HUD; export a result first if you want to keep it.

Damage capture and screen-OCR observation have separate controls. **Stop observation** and F8 stop OCR while leaving the meter running. The legacy **Stop** button in Expert controls stops both OCR observation and damage capture. F9 resets only the boss encounter. Closing Sentinel shuts down its owned meter worker.

## Table and measurements

The table displays **Player**, **Class**, **DPS**, **Damage** and **Share**, ranked by DPS. The summary shows the target label, elapsed time and totals for the displayed rows. When captured damage spans multiple targets, the counter can show **All targets**. A missing name uses a numeric label or an unidentified target.

All rows use the same interval, beginning with the first retained damage record and ending at the current measurement time. Each player's DPS is their recorded damage divided by that shared interval. It is a cumulative average, including quiet time, rather than a separate timer for each player's active attacks. Share is each displayed player's fraction of the displayed damage total.

The current controls show the captured counter across targets. They do not expose party-only or selected-target filtering. Observed actors can include non-party players until roster and identity evidence are confirmed. A displayed class, local-player marker or summon attribution can remain incomplete; missing records do not establish zero damage.

The damage HUD shows up to eight rows. The main table retains all rows in the current snapshot.

## When player names are pending

Damage and player names arrive in separate server records. Enabling capture after login can miss the earlier character record, so the meter may show damage beside a numeric label such as **Player 1234**. The tab and damage HUD show a names-pending hint while rows are unidentified.

Keep the meter enabled during an area change or login so it can receive fresh name and character records. In version 0.6.4, an explicit name record updates the matching player-ID rows without resetting their damage. The update can appear even when no further damage is dealt. Your own character label requires its explicit local-character record; the highest damage row or an inferred class does not identify you.

The meter uses observed IDs to match names. A new or reused ID does not justify assigning a newly observed name to unrelated older anonymous rows. Those rows can remain in the accumulated counter after an area change. Once the new names arrive, **Reset damage counter** is optional if you want a fresh named counter. Export the existing rows first if you want to keep them. Resetting is not required for a name update on the same confirmed ID.

Receiving a name confirms that record's label, not complete party membership, summon ownership or current-build damage accuracy. Missing records and unsupported protocol changes can still leave names unavailable.

## HUD and controls

- **Show damage HUD** shows or hides the separate damage overlay.
- **Lock damage HUD / click-through** lets mouse clicks pass through. Clear it to drag the HUD, then lock it again for play.
- **Save settings** in Setup retains the damage HUD position, visibility and lock setting. It does not enable capture automatically at the next launch.
- **Reset damage counter** clears the current displayed counter. Its next interval begins with the next decoded hit. After finishing a run, reset starts a new run.
- **Finish current run** freezes the current run and stops adding damage to it. Capture remains enabled. Export the result, then reset to measure another run.
- **Export displayed rows** saves a UTF-8 CSV with player name, actor ID, class, DPS, damage, share, local-player marker, elapsed seconds, target and source label. It exports the displayed snapshot; it is not a saved replay or complete combat log.
- **Run simulated meter demo** replaces live capture with generated players and damage records. The table and HUD label this **SIMULATED DEMO**. Npcap and a running game are unnecessary for the demo.

F7 and the **Combat HUD** checkbox control the three boss-warning surfaces. Use **Show damage HUD** for the damage overlay.

## Source status and limits

The status line reports capture state, received packet count and decoded damage-record count. Readings are hidden when the source is unavailable, fails validation or stops providing fresh snapshots for more than three seconds. Check the status before interpreting an empty table.

The parser's pinned reference and annotated fixtures describe **EU early access, 30 September 2026, TCP port 13328**. This is upstream calibration evidence. Current EU build compatibility, complete combat coverage and damage accuracy have not been validated in a live encounter. A game update can change the protocol while screen OCR continues working.

Player names, classes, local-player identity, party membership and summon ownership depend on available decoded metadata. PvP and complete healing or defense analysis are outside the current meter's supported display. Boss and skill-name catalogs are not bundled with this worker, so numeric labels are expected where decoded names are unavailable.

If Npcap is missing, enabling **Damage meter** offers guided setup. If you cancel, setup fails, capture access is denied or a reboot is required, readings remain off and the status explains the next step. Resolve the reported prerequisite or permission issue, then re-enable **Damage meter**. If the bundled backend is missing, re-extract the complete Sentinel folder. The simulated demo previews the table, HUD and controls independently of live capture; it does not validate current-game traffic.

## Source provenance and notices

Sentinel adapts MIT-licensed source from [xzHannes/aion-companion](https://github.com/xzHannes/aion-companion) at commit `dbc3c275fe1846c8a98b531b966d227cb4d0ca02`. Its attributed parser subset originates from SkeeveAN/Aion-DPS-Meter at `ea8fca7e0b629a46da8ce8560462f52e05a0ffeb`. Sentinel's local worker entry point and snapshot interface are adaptations around those sources, retained in the maintainers' project.

The protected portable release includes provenance in `meter/NATIVE_NOTICE.md` and licenses under `meter/licenses`; it does not include Sentinel's adapted implementation source. SharpPcap 6.3.0 uses MIT. Unmodified PacketDotNet 1.4.7 uses MPL-2.0 and is compiled into the NativeAOT worker; its covered source remains available through `meter/licenses/dependencies/PacketDotNet-1.4.7/SENTINEL-SOURCE-AVAILABILITY.md`. Npcap is supplied separately by its publisher. LGPL Qt/PySide6 source and replacement instructions are under `licenses/Qt/`.
