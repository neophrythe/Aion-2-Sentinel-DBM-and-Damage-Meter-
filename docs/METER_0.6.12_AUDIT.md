# Damage meter correction — 0.6.12 Unfinished Beta

A user reported that two other meters agreed while Sentinel was about 5,000 lower in a Deus encounter. Whether this concerned DPS or total damage and the exact comparison interval remain unknown. The fixes below address demonstrated source defects; they do not establish the cause of that particular result.

## Measurement interval

The previous worker always displayed counter/current-run snapshots ending at the current clock. Boss death did not freeze that default DPS display. At 600,000 captured damage over 20 seconds, the correct interval gives 30,000 DPS; extending the interval by four idle seconds gives 25,000 DPS with identical damage. This explains a possible 5,000 discrepancy without a missing damage record.

The pinned MIT Aion Companion reference uses automatic boss-attempt selection and a twelve-second inactivity policy. Sentinel now adapts that display behavior while preserving the separate cumulative counter. Finished attempts freeze; resumed unfinished fights include their elapsed quiet phase. The worker reports the displayed scope, start/end interval and DPS clock, and the control window offers a comparison export. No multiplier or artificial damage addition is used.

## Capture continuity

The 0.6.11 encounter bridge reset the shared decoder and TCP reassembler when incoming stream keys alternated, or when authoritative socket-owner evidence changed or temporarily disappeared. Alternating connections could consequently discard a split damage frame or character/summon metadata. The reassembler already handles multiple TCP streams independently.

Stream and socket-owner changes now invalidate only the supplementary encounter observations. Buffered transport data and existing damage metadata continue. After invalidation the bridge requires a fresh NPC spawn before relinking HP to a visible target; cached meter identity cannot recreate the supplementary binding. This correction does not add protocol opcodes or claim complete current-build decoding.

## Verification and remaining evidence

Focused native cases exercise split/out-of-order packets, alternating streams, retransmissions, owner loss/reappearance, summon attribution, finished DPS, late hits, new combat, reset and scope selection. Python checks cover Deus identity selection, the UI display contract, comparison export and existing warning behavior. Actual counts and exact source/native hashes accompany the local build evidence.

For a live comparison, use the same fight, reset/start point, target, party selection and player row. Preserve both total damage and DPS with the elapsed interval. The named comparison meters and the exact Deus boss are still needed to establish whether a remaining discrepancy is decoding, attribution or measurement scope.

Source: MIT [Aion Companion](https://github.com/xzHannes/aion-companion/tree/dbc3c275fe1846c8a98b531b966d227cb4d0ca02), local `Worker/MeterView.cs`, `Worker/Program.cs`, `Adapted/LiveCaptureService.cs` and their regression cases. Current live-game agreement remains pending.
