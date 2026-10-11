# Sentinel 0.6.10 — automatic beginner mode

Unfinished Beta. Active development — gameplay validation pending. No new application, executable, UI, OCR, functional, unit, integration or live tests were run.

Extract the complete package into a writable folder and open AION-Sentinel.exe. The default window has three controls:

- **Combat HUD** shows or hides boss-warning overlays.
- **Start observation / Stop observation** starts or stops screen observation. Bring the English AION2 client to the foreground. Stopping observation leaves the optional damage meter running.
- **Damage meter** starts or stops the integrated meter and its damage overlay. The capture adapter is selected automatically. If Npcap is absent, guided setup is offered; capture still requires Npcap and sufficient permissions. Source errors are shown in the main window.

## First use of the damage meter

Enable **Damage meter** when you want live readings. If Npcap is already installed, Sentinel skips guided setup and starts the capture worker. If it is absent, choose **Set up Npcap** in **Set up damage capture** to consent to downloading the fixed **Npcap 1.89** installer from [the official publisher](https://npcap.com/#download). Sentinel opens the visible installer and the normal Windows elevation prompt. Review and accept the publisher's license and choose installation options yourself; Sentinel does not silently install the driver or accept the license for you. The installer is not included in the archive.

Choose **Cancel** to decline setup, or cancel its progress dialog to stop the download. Cancelling setup, declining elevation or an installation failure leaves the meter off. You can continue using screen OCR. If a reboot is required, Sentinel leaves capture off and does not restart Windows; reboot when convenient, then enable the meter again. Otherwise, it rechecks the required capture components and retries the worker. An administrator-only Npcap installation can still require administrative capture rights.

The 0.6.10 setup flow is implemented but has not undergone new application, functional, integration or live tests.

## Automatic observation

Names, levels, locations, compatible profiles and standard target/HP/cast search regions are found automatically. Normal enemies remain excluded. Runtime automatic settings ignore stale manual rectangles without deleting the saved expert preferences. Profile rule edits and disabled choices remain respected. Warning sounds and available English speech use the stored defaults.

If a confirmed boss/location has several compatible Explore/Conquest profiles and the difficulty is still unknown, only identical, enabled, NPC-owned skill-text warnings shared by every surviving variant can be used. Two distinct complete-line observations are required. Shared mode has no variant HP hints or timers and is not saved over an actual variant's profile. If no safe common rules exist, warnings wait for more evidence.

Unknown names, absent minimap labels, ambiguous normal/summon candidates and unseen cast text do not become guessed warnings. Identity recognition cannot fill missing mechanic data. Some target profiles have no automatic rules. The observer does not control the game.

**Advanced → Expert controls** reveals the full setup, manual profile chooser, individual cues, library, recordings and meter diagnostics. These are optional tools. The simple mode does not require region selection, profile choice, a data-feed file, class choice, adapter selection or manual countdown configuration. A heavily customized or hidden game HUD may require expert calibration.

F7 toggles the combat HUD. F8 toggles observation independently of meter capture. F9 retains the encounter-reset shortcut. F10 remains available to the game. The main controls remain usable when a shortcut is occupied.

The meter starts with all captured actors and targets. Expert controls offer captured-target selection and a confirmed-party filter; pending roster identity leaves observed actors visible. Player names appear when corresponding identity records arrive; keep capture running through login or an area change if names are pending. It does not promise an isolated DPS board for every ordinary boss.

The separate damage HUD can be hidden, locked, scaled, made more transparent or recentered without stopping capture. Local history distinguishes runs and boss attempts, including the reason they ended. These reports overlap and must not be added together. Synthetic demo reports are marked and hidden by the default history filter.

Published broadcast and player-debuff responses need fresh text in their own channel and the correct encounter context. Cast estimates need a visible measured target cast. Learned recurrence estimates need several completed live attempts and an explicitly confirmed phase; current screen observation alone does not provide that phase. Missing evidence leaves the corresponding feature inactive. These conditions do not require extra beginner controls and do not establish complete fight coverage.
