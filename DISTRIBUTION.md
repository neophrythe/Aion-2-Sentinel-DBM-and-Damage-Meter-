# Distribution and dependency notices

Created by **Neophrythe & Dr.Tatsu**.

This repository publishes Sentinel binary releases, documentation and promotional material. Sentinel's implementation source and private build material are not included, and publication here does not grant an open-source license for that implementation. Contact [neophrythe](https://github.com/neophrythe) for implementation reuse or redistribution questions.

The complete portable archive contains the third-party notices and applicable licenses. These must remain with the distributed application. Third-party license rights are separate from Sentinel's implementation status.

- Qt/PySide6/Shiboken shared libraries retain their applicable terms, source-availability information and library-replacement instructions under `licenses/Qt/`.
- The native meter retains its MIT notices and dependency notices, including covered PacketDotNet MPL source availability under `meter/licenses/`.
- The reviewed public boss reference retains its MIT notice and source attribution.
- OCR models and other packaged dependencies retain their own notices under `licenses/` and the supplied source-availability documents.
- Npcap is installed separately and is not redistributed in the archive. In 0.6.7, guided setup downloads the fixed official Npcap 1.89 installer only after user consent, checks the pinned SHA-256 and publisher signature, and opens the visible installer with Windows elevation. The user reviews its license and selects its options; no silent installation or automatic license acceptance is performed.

Readable Sentinel implementation source, private signing keys, local settings, captures and internal research are excluded from public release assets. An internal RSA-PSS file manifest checks critical packaged files. It is separate from Windows Authenticode signing and is not a guarantee against reverse engineering.

AION and AION2 names and related trademarks belong to their respective owners. Sentinel is independent of NCSOFT and Deadly Boss Mods; official approval and account-safety guarantees have not been established.
