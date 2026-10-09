# Quick start — 0.6.6 preview

The current build is implemented and untested. Download it from the [release page](https://github.com/neophrythe/Aion-2-Sentinel-DBM-and-Damage-Meter-/releases/tag/v0.6.6), then extract the complete folder into a writable location.

Open `AION-Sentinel.exe`. The default view has three controls:

| Control | Action |
| --- | --- |
| Combat HUD | Show or hide boss warnings. |
| Start / Stop observation | Start or stop local screen observation; the optional damage meter continues independently. |
| Damage meter | Start or stop integrated damage capture and its overlay. |

Bring the English AION2 client to the foreground after starting observation. The standard name, level, location, HP and cast search areas follow the game window automatically. Normal targets receive no boss warnings. Profiles switch when compatible identity and location evidence is available.

For damage capture, install Npcap separately. The worker selects the capture adapter automatically. If character names are pending, keep it enabled through login or an area change so fresh identity records can arrive.

F7 controls the HUD, F8 observation and F9 encounter reset. Use the window controls if a shortcut is already occupied.

Optional tools are under **Advanced → Expert controls**. Custom or hidden game HUD layouts may need expert calibration. The current source inventory cannot provide complete mechanics or measured countdowns for every boss.

See [troubleshooting](FAQ.md) and [coverage](COVERAGE.md). Keep all files from one version together; do not replace individual runtime files from another release.
