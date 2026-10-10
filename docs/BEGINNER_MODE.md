# Sentinel 0.6.8 — automatic beginner mode

Created by **Neophrythe & Dr.Tatsu**.

Unfinished Beta. Active development — gameplay validation pending. Compilation and package integrity have been checked; these do not validate gameplay behavior.

Extract the complete package into a writable folder and open AION-Sentinel.exe. The default window has three controls:

- **Combat HUD** shows or hides boss-warning overlays.
- **Start observation / Stop observation** starts or stops screen observation. Bring the English AION2 client to the foreground. Stopping observation leaves the optional damage meter running.
- **Damage meter** starts or stops the integrated meter and its damage overlay. The capture adapter is selected automatically. If Npcap is absent, guided setup is offered; capture still requires Npcap and sufficient permissions. Source errors are shown in the main window.

## First use of the damage meter

Enable **Damage meter** when you want live readings. If Npcap is already installed, Sentinel skips guided setup and starts the capture worker. If it is absent, choose **Set up Npcap** in **Set up damage capture** to consent to downloading the fixed **Npcap 1.89** installer from [the official publisher](https://npcap.com/#download). Sentinel opens the visible installer and the normal Windows elevation prompt. Review and accept the publisher's license and choose installation options yourself; Sentinel does not silently install the driver or accept the license for you. The installer is not included in the archive.

Choose **Cancel** to decline setup, or cancel its progress dialog to stop the download. Cancelling setup, declining elevation or an installation failure leaves the meter off. You can continue using screen OCR. If a reboot is required, Sentinel leaves capture off and does not restart Windows; reboot when convenient, then enable the meter again. Otherwise, it rechecks the required capture components and retries the worker. An administrator-only Npcap installation can still require administrative capture rights.

The guided setup flow remains available in 0.6.8; its application behavior and live capture still require validation.

## Automatic observation

Visible remaining seconds or a changing target-cast bar can supply a **cast (est.)** countdown and an estimated cast-ending heads-up. No new beginner control is required. A skill name alone does not start a clock; hidden or ambiguous cues can leave it absent. These estimates do not time individual waves or repeat sequences. See [cast timing](CAST_TIMING.md).

Names, levels, locations, compatible profiles and standard target/HP/cast search regions are found automatically. Normal enemies remain excluded. Runtime automatic settings ignore stale manual rectangles without deleting the saved expert preferences. Profile rule edits and disabled choices remain respected. Warning sounds and available English speech use the stored defaults.

If a confirmed boss/location has several compatible Explore/Conquest profiles and the difficulty is still unknown, only identical, enabled, NPC-owned skill-text warnings shared by every surviving variant can be used. Two distinct complete-line observations are required. Shared mode has no variant HP hints or timers and is not saved over an actual variant's profile. If no safe common rules exist, warnings wait for more evidence.

Unknown names, absent minimap labels, ambiguous normal/summon candidates and unseen cast text do not become guessed warnings. Identity recognition cannot fill missing mechanic data. Some target profiles have no automatic rules. The observer does not control the game.

**Advanced → Expert controls** reveals the full setup, manual profile chooser, individual cues, library, recordings and meter diagnostics. These are optional tools. The simple mode does not require region selection, profile choice, a data-feed file, class choice, adapter selection or manual countdown configuration. A heavily customized or hidden game HUD may require expert calibration.

F7 toggles the combat HUD. F8 toggles observation independently of meter capture. F9 retains the encounter-reset shortcut. F10 remains available to the game. The main controls remain usable when a shortcut is occupied.

The meter uses its existing aggregate-run measurement and decoded run-boundary resets. It does not promise an isolated DPS board for every ordinary boss. Player names appear when corresponding identity records arrive; keep capture running through login or an area change if names are pending.
