# Sentinel 0.6.7 native binary distribution

Created by **Neophrythe & Dr.Tatsu**.

This portable build compiles Sentinel's own implementation to native code
and uses its bundled NativeAOT damage-meter worker. It excludes Sentinel's
readable source, tests, generated C files, build logs and debug symbols from
the public application archive. The project's local source and build evidence
remain available to its maintainers.

Native compilation raises the effort required to reconstruct the implementation.
It cannot make reverse engineering impossible. Public reference data,
configuration formats and third-party libraries remain inspectable.

An RSA-PSS-SHA256 release manifest checks Sentinel's own critical files
before normal startup. This detects changed or incomplete protected files;
a determined local attacker can modify the verifier itself. This internal
release signature is **not Windows Authenticode signing** and does not
establish Windows publisher trust. Extract the complete archive to restore
a modified or missing protected file.

The user-facing controls remain F7 for the Combat HUD, F8 for Start / Stop
observation independently of the meter, and F9 for encounter reset. User
settings, custom profiles and recordings remain editable in the application's
data folder. Live damage capture requires a separate Npcap installation.
When Npcap is absent, enabling the meter offers guided download of the fixed
Npcap 1.89 installer from its official publisher, after user consent. The
normal visible installer and Windows elevation prompt remain under the user's
control, including license acceptance and installation options. No capture
driver or installer is included in this archive, and no silent installation
is performed. Cancellation, failure or a required reboot leaves capture off;
Sentinel does not automatically restart Windows.

Third-party copyright notices and licenses accompany the binary. Qt/PySide6
shared libraries remain replaceable under their LGPL terms; see
licenses/Qt/SOURCE-AVAILABILITY.md and licenses/Qt/RELINKING.md. PacketDotNet's
covered MPL source remains available through the notice under meter/licenses/.
The separate protected implementation does not restrict those source or
library replacement rights.

The 0.6.7 portable archive is an Unfinished Beta. Packaging checks its size
against 100,000,000 bytes, extraction CRC, payload SHA-256 values and own-file
signatures. These structural checks do not establish functional readiness:
no new application, functional, OCR, meter, unit, integration or live-game tests
were run for this version.
Compression is lossless and retains the bundled OCR models. See
RELEASE_0.6.7_BETA.md and the separate archive status and manifest for the
measured packaging results and validation limits.
