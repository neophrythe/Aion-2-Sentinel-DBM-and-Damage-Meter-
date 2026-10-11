# Sentinel 0.6.13 — Unfinished Beta

Created by **Neophrythe & Dr.Tatsu**. AION 2 EU / International, English client.

- DPS uses the first-to-last selected damage interval with a one-second minimum.
  Short pauses no longer depress the displayed value; resumed phases retain
  their elapsed pause.
- Recognised summons remain visible while ownership is unresolved. Later owner
  information can merge earlier damage without adding it twice. Entity
  generations protect against reused IDs; ambiguous same-class parties are
  left unresolved.
- Boss self-healing no longer inflates player damage in the published MIT case.
  Compact damage ticks and bounded nested compressed bundles are supported.
- DoT ticks add damage without inflating direct-hit and critical counters.
- HUD and control window identify boss-only versus all-target damage.
  Comparison exports include the actual interval and DPS divisor.
- Previous Deus recognition and capture-continuity corrections are retained.

Focused offline/native checks accompany this exact build. Live agreement with
other meters and complete current-game coverage remain pending. See
METER_0.6.13_AUDIT.md and BETA_RELEASE.json. The earlier competitor comparison
and 0.6.12 audit are historical baseline documents.

Extract the complete package and run AION-Sentinel.exe. Keep its folders together.
Npcap is separately installed only for the optional Damage meter. Own-file
integrity signatures are not Windows Authenticode signatures.

182 Python checks and 88 native worker assertions passed on this build. Complete frozen-application gameplay and the reported live DPS difference still require a matching encounter comparison.

Archive: AION-Sentinel-0.6.13-beta-windows-x64.7z · **95,533,011 bytes** (95.53 MB / 91.11 MiB), 442 files.

SHA-256: `b90481196a5d8e6b045d80c8a33db459127f9c3d5082536e31c74d8e3a472961`
