# Road map

This page provides a short and likely not entirely accurate selection of topics that will be in focus sooner or later. All-time topics are not added here, unless they are a major topic of a planned release or milestone, namely reducing false positives and (minor) fixes in general. From "Planned" on it gets shifty.

For a more detailed explanation or discussion of future design issues see the Design (TODO: link) page.

# Current focus
* A recommended release, just to have one this year. (Depends on: Feedback.)
* Possibly quick-fix false positives with survivalfly (sprint+jump) and passable. Issues around 2017-04-XX.

# Scheduled
Topics that will be tackled soon, no guarantee on order.
* Moving checks: set back policy refinements.
    * suggestSetBack instead of setting it within LOWEST event priority. Really set on MONITOR, only if not cancelled.
    * Unified handling of specialties with set back locations for all moving checks (not within survivalfly).
    * One spot to decide how to alter scheduled set back locations (voidtovoid, forcefall, downtoground).
    * Actually implement at least one new set back policy (forcefall or downtoground).
    * (Let checks and config select which alterations are allowed.)
* Further examine role of UNKNOWN (vanilla) server teleport. Consider to always cancel them if setting into blocks, and cancel the teleport and _schedule_ a set-back for on-tick execution. (+ config)
* Data storage overhaul: Concentrate relevant data inside of PlayerData (check data - possibly also permission cache, exemption, ...).
    * Might implement permission caching, possibly first just for survivalfly, to see if/how it pays off.
* Fight checks, penalty actions: implement more penalty actions, allow use in fight checks.
* Fight checks, loop checks design.
    * Consider to implement generic loop checks, that run as many sub checks as are passed.
    * Consider running two rounds of loop checks, where the first one will confine the latency window in a rather efficient way.
    *Possibly  redo LocationTrace + pvp vs. pve config for loop checks
* Horizontal piston moving with players.
* SurvivalFly: sprint+jump and special case refinement. Possibly recode with new style workaround class use.

## Planned
Topics that likely will follow up, no guarantee on order, might slip further away.
* Data expiration - be able to remove lots of stored data on logout, possibly add a minimized offline data object within PlayerData (and possibly persist on disk, if set so).
* Vehicle checks refinements: passable? Which ones to check + configure? Actual speed limiting. Pistons / block changes, at least simplistic.
* Interact ray-tracing: Use passable ray-tracing, possibly make it ray-tracing per block.
* Packet inversion problem: interact before look.
* Refine onground checks (spider vs. stuck with bounding box).
* Change isOnGround to a more flexible method (allow for distanceToGround), or provide an extra method.
* Block compatibility config and defaults: add named sets of blocks to set the same flags for many, with activation flag.
* Better horizontal velocity handling.
* More packet level checks (tab-complete, nasty data, strip content from books, items).
* Checks against unwanted content exposure (prevent sending content of books, item names, other).
* Detect "more inventory".
* Detect sending too few packets.
* More long term event frequency tracking.

## Planned (at some distance)
Pretty hard targets, but too far off the schedule to give any ETA.
* Add check/notification for players not using any velocity (mostly sf), at least start to log it for testing. [A simple first thing is in debug logs, not a check.]
* _"Full" UUID compatibility_. Better handling of data with UUIDs, API. Cache policy for name<->uuid mappings.
* Refine logging options in general (rolling files, manual entries, backups).
* Better mod support for arbitrary blocks and tools. Includes cleanup of block-properties-handling.
* Ingame configuration management (convenience, comparison, suggestions, hot-fixes).
* Velocity handling: Switch to 3d-entries with "exact" per-axis/direction counting.
* Per player fake blocks (via per player block cache or via BlockChangeTracker).
* Checks for creative mode exploits (enchantments, clickable text). [Specialized plugin(s) exist, postponed.]
* Moving/morepackets: Further invalidate past intervals to be more precise. Maybe include latency estimates.
* A log viewer with specialized features. E.g. confine view to one player + name/uuid mentioned. Interpret moving debug logs and find violations and patterns or custom defined sequences. Process large logs in a more or less smart way.
* Refine debug logging: Allow per-player or group files. Consider triggers to auto-start debug logging. Consider hooking into the debug stream in-game (!), possibly with reduced data. Might add a binary format, replay? Post-violation debug log - keep in memory and log on trigger/demand.
* Event/pattern engine: Allow pattern detection and/or automata-based configurable meta checks.
* Full core-recode. API-independent core + on-the-fly adding and removal of checks and other.
