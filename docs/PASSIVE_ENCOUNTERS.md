# Passive encounter evidence — Sentinel 0.6.11

The optional Damage meter can supply fresh runtime actor IDs, static NPC IDs,
raw current HP and observed death/revival to Sentinel's encounter observation.
The standard beginner controls remain Combat HUD, observation and Damage meter.
Boss warnings still follow the visible English target and location.

Only the selected capture adapter publishes facts. Each capture/connection/run
scope has a separate epoch and increasing sequence. Connection or character
changes, actor reuse, malformed boundaries, queue overflow and stop/reset clear
the bindings. The UI rejects stale, delayed and duplicate observations and
requires two distinct capture timestamps before using a target binding.

An original read-only Windows IP Helper query matches an established TCP
connection's complete local/remote address and port tuple. A unique owning
process must currently be AION2. Ownership expires after one second and is
rechecked; a changed process/creation time starts a new scope. The captured
foreground game window supplies its independently verified PID. Native identity
can supplement automatic profile selection only when these PIDs agree and a
fresh English target name exactly matches the NPC reference. Nearby spawns,
unlinked connections and ambiguous same-name actors cannot select a profile.

The Expert Live page displays actor ID, NPC ID, raw HP and link status. Raw HP
has its own freshness clock. Identity updates do not extend it; death remains
until newer positive HP evidence within that actor lifetime. A linked observed
target death clears its warnings while Sentinel waits for a live visible target.
Capture-derived target facts are retained in local observation recordings for
replay; live packets are never mixed into a replay. Replay does not train live
recurrence learning.

The native worker has a conservative, generated English boss identity table
from exact existing catalog/profile/NPC joins. Ambiguous names, instances and
contradictory IDs are excluded. This supplies target names and catalogued boss
lifecycle classification; it is not a complete mechanic database.

The stream supplies no authoritative maximum HP, percentage, map, phase,
cast-start timestamp or wave-impact schedule. Highest previously seen HP is
never treated as maximum HP. Damage-derived skill labels are excluded from cast
prediction. Protocol interpretation remains version-dependent, and a socket
owner match does not validate packet semantics or every boss mechanic.

Fresh positive HP can keep an already damaged catalogued boss attempt open
during a no-damage mechanic, within the existing timeout. It adds no damage and
does not change the DPS denominator. Compile/source/package checks do not prove
gameplay behavior; this remains an **Unfinished Beta**.
