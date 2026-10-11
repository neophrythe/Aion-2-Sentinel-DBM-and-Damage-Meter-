# Quick start — 0.6.13 Unfinished Beta

Created by **Neophrythe & Dr.Tatsu**.

This is the 0.6.13 Unfinished Beta. Active development — gameplay validation pending. Compilation and package integrity have been checked; these do not validate gameplay behavior. Download it from the [release page](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases/tag/v0.6.13), then extract the complete folder into a writable location.

Open `AION-Sentinel.exe`. The default view has three controls:

| Control | Action |
| --- | --- |
| Combat HUD | Show or hide boss warnings. |
| Start / Stop observation | Start or stop local screen observation; the optional damage meter continues independently. |
| Damage meter | Start or stop integrated damage capture and its overlay. |

Bring the English AION2 client to the foreground after starting observation. The standard name, level, location, HP and cast search areas follow the game window automatically. Normal targets receive no boss warnings. Profiles switch when compatible identity and location evidence is available.

A visible, uniquely recognized target skill with explicit remaining seconds or a changing cast bar can add a **cast (est.)** countdown and an estimated cast-ending heads-up. A skill name alone never starts a clock. Missing or ambiguous cast displays can leave it absent; individual waves and repeat sequences remain outside this estimate. No extra beginner control is required. See [cast timing](../docs/CAST_TIMING.md).

For live damage readings, enable **Damage meter**. If Npcap is already installed, Sentinel skips setup and starts its worker. Otherwise, choose **Set up Npcap** to consent to downloading the fixed **Npcap 1.89** installer from the official publisher. Sentinel checks its pinned SHA-256 and publisher signature before opening the normal visible installer with Windows elevation. Review the publisher's license and choose its installation options yourself. The installer is not bundled and installation is not silent.

Choose **Cancel** if you do not want setup. Cancelling, declining elevation or installation failure leaves the meter off; screen OCR stays available. A required reboot does not restart Windows automatically. Reboot when convenient, then enable the meter again. Otherwise, Sentinel rechecks capture components and retries its worker. Capture permissions can still prevent readings; manual installation from [Npcap's official download page](https://npcap.com/#download) is also available.

The worker selects the capture adapter automatically. If character names are pending, keep it enabled through login or an area change so fresh identity records can arrive. See [complete meter setup and measurement limits](../docs/DAMAGE_METER.md).

F7 controls the HUD, F8 observation and F9 encounter reset. Use the window controls if a shortcut is already occupied.

Optional tools are under **Advanced → Expert controls**. Custom or hidden game HUD layouts may need expert calibration. The current source inventory cannot provide complete mechanics or measured countdowns for every boss.

See [troubleshooting](FAQ.md) and [coverage](COVERAGE.md). Keep all files from one version together; do not replace individual runtime files from another release.
