# Road map

This page provides a short and likely not entirely accurate selection of topics that will be in focus sooner or later. All-time topics are not added here, unless they are a major topic of a planned release or milestone, namely reducing false positives and (minor) fixes in general. From "Planned" on it gets shifty.

For a more detailed explanation or discussion of future design issues see the Design (TODO: link) page.

# Current focus
* Fight checks (implement penalty actions, allow use in fight checks, redo LocationTrace + pvp vs. pve config for loop checks).
* Minimum piston compatibility, onground checks (spider vs. stuck with bounding box).
* Milestone: Refine fight checks (false positives, precision): 2016-02-14 [Postponed or split into several iterations due to bugs, possibly 1.9.]

# Scheduled
Topics that will be tackled soon, no guarantee on order.
* Keep track of pistons moving blocks in order to reduce false positives (First the minimum for pistons with survivalfly, later block change tracking for survivalfly and passable in general).
* Horizontal speeding.
* 1.9 support (mostly allow creativefly model configs to confine ascend/descend and allow fall-damage, let it handle levitation and elytra, off-hand to mcAccess).
* Interact ray-tracing: Use passable ray-tracing, possibly make it ray-tracing per block.
* (Stabilize changes vs. features for a fully recommended release.)

## Planned
Topics that likely will follow up, no guarantee on order, might slip further away.
* Block compatibility config and defaults: remove default blocks, add named sets of blocks to set the same flags for many, with activation flag. Add a disabled by default entry for all blocks changing shape with redstone signals.
* Data expiration - add minimized "offline" data, to be able to remove lots of stored data on logout.
* Better horizontal velocity handling.
* Moving checks data refinement. Keep track of edge data for 3 or more moves (better for special case false positives).
* More packet level checks (tab-complete, nasty data, strip content from books, items).
* Checks for creative mode exploits (enchantments, clickable text).
* Checks against unwanted content exposure (prevent sending content of books, item names, other).
* Detect "more inventory".
* Detect sending too few packets.
* More long term event frequency tracking.

## Planned (at some distance)
Pretty hard targets, but too far off the schedule to give any ETA.
* Allow making doors safe (e.g. enable ray-tracing by keeping track of redstone changes).
* Add check/notification for players not using any velocity (mostly sf), at least start to log it for testing.
* _"Full" UUID compatibility_. Better handling of data with UUIDs, API. Cache policy for name<->uuid mappings.
* Concentrate data and configs in DataManager (+WorldData + WorldConfig?) and PlayerData. Lazy and aggregated data removal (for COWs).
* Refine logging options in general (rolling files, manual entries, backups).
* Better mod support for arbitrary blocks and tools. Includes cleanup of block-properties-handling.
* Ingame configuration management (convenience, comparison, suggestions, hot-fixes).
* Velocity handling: Switch to 3d-entries with "exact" per-axis/direction counting.
* Moving/morepackets: Further invalidate past intervals to be more precise. Maybe include latency estimates.
* Refine debug logging: Allow per-player or group files. Consider triggers to auto-start debug logging. Consider hooking into the debug stream in-game (!), possibly with reduced data. Might add a binary format, replay? Post-violation debug log - keep in memory and log on trigger/demand.
* Event/pattern engine: Allow pattern detection and/or automata-based configurable meta checks.
* Full core-recode. API-independent core + on-the-fly adding and removal of checks and other.
