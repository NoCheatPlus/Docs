# Road map

This page provides a short and likely not entirely accurate selection of topics that will be in focus sooner or later. All-time topics are not added here, unless they are a major topic of a planned release or milestone, namely reducing false positives and (minor) fixes in general. From "Planned" on it gets shifty.

For a more detailed explanation or discussion of future design issues see the Design (TODO: link) page.

# Current focus
* Follow up release with bug fixes, expecting more feedback due to releasing both on dbo and spigotmc.
* Possibly quick-fix false positives. Issues around 2017-04-XX.
    * survivalfly: sprint+jump
    * passable: uncertain, possibly retry with other axis order under certain conditions, such as moving down.
* Evaluate: hacc with another slightly longer term tracking with extra limit - might allow a lower limit.
* Decision for next topic between:
    * Fight checks (multiple iterations pending).
    * Data storage overhaul (multiple iterations pending).
    * set back policy (a) better cross-plugin compatibility b) new policies)

# Scheduled
Topics that will be tackled soon, no guarantee on order.
* Fight checks, penalty actions: implement more penalty actions, allow use in fight checks.
* Check data access: Implement (more) fine grained data removal for the remaining check types.
* Fight checks, loop checks design.
    * Implement generic loop methods, not depending on certain checks.
    * Have multiple rounds with differing checks (1. fastest checks + determine latency window 2.-X. Further checks to refine window Last: checks that just use the latency window + best guess).
    * Possibly  redo LocationTrace + pvp vs. pve config for loop checks.
* Data storage overhaul: Concentrate relevant data inside of PlayerData (check data - possibly also permission cache, exemption, ...).
    * Internal change (breaking): Store all per-player check data inside of PlayerData, alters interfaces and factories for CheckData factory (a real factory is needed, PlayerData will implement something like I(Generic)DataStore or similar).
    * Might implement permission caching, possibly first just for survivalfly, to see if/how it pays off.
* Moving checks: set back policy refinements.
    * suggestSetBack instead of setting it within LOWEST event priority. Really set on MONITOR, only if not cancelled.
    * Unified handling of specialties with set back locations for all moving checks (not within survivalfly).
    * One spot to decide how to alter scheduled set back locations (voidtovoid, forcefall, downtoground).
    * Actually implement at least one new set back policy (forcefall or downtoground).
    * (Let checks and config select which alterations are allowed.)
* Fight checks / latency:
    * Refine / implement-at-all: Make more use of a latency window - cross check with other checks and data sources (!).
    * Have a sequence of past latency estimates+windows and compare that of the attacker to the LocationTrace (latency _at that time_).
    * Update the LocationTrace on MONITOR (ensure), include the latest possible time stamp.
* Fight checks: Refine and implement new.
    * Refine loop checks (if not already done), to make full use of capabilities of the loop.
    * Implement new (planned) checks, like targeting/difficulty.
    * Test + sketch out further directions (no joke :p).
* Horizontal piston moving with players.
* SurvivalFly: sprint+jump and special case refinement. Possibly recode with new style workaround class use.
* Further examine role of UNKNOWN (vanilla) server teleport. Consider to always cancel them if setting into blocks, and cancel the teleport and _schedule_ a set-back for on-tick execution (+ config). Could touch questions with passable/phase, if those questions exist with the default configuration at all.
* Evaluate: command driven state machines (feed/trigger via actions, machines and further data queries via config).
* Evaluate: model configs (reference other configurations to override selected areas of the configuration, without altering the configurations, just apply model with id 'abc' from 'modelconfigs/xyz.yml').

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
