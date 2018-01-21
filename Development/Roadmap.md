# Road map

This page provides a short and likely not entirely accurate selection of topics that will be in focus sooner or later. All-time topics are not added here, unless they are a major topic of a planned release or milestone, namely reducing false positives and (minor) fixes in general. From "Planned" on it gets shifty.

For a more detailed explanation or discussion of future design issues see the Design (TODO: link) page.

# Current focus
* Primary
    * Topic
        * Unify NCP and cncp.
        * More consistent and easier to use exemption framework (prevent interference, register auto-removal and other side conditions for easier setting up).
        * Work towards centralized data/config access and storage (one PlayerData object to hold them all).
    * Restructure NCP towards a) combining NCP and cncp in one plugin b) work towards a unified PlayerData structure.
        * Add a CheckTypeTree instance to PlayerData. This provides some kind of milestone, as per check type data will be stored here, allowing to easily set up thread-safe reading at least. 
        * New non-static implementation of exemption, accessible via PlayerData.
            * Reliable for cross-plugin use, reference multiple exemption entries by registered ids, less ambiguous.
            * Built-in features, such as automatic event wrapping (compare to cncp std. hooks for block break and the like), automatically evaluated conditions for unregistering (ends with tick, event soandso at MONITOR level, player leaves the server, world change, ...). Essentially the generic features of cncp plus extensions on top of the new event registry are added to NCP directly, without even breaking compatibility with older versions of cncp.
        * Either re-implement cncp hooks with reflection (allow easy replacing, if someone wants to write a better hook), or include as NCPCompatExt inside of NCP.
        * Evaluate: Use a generic instance registry per player data (due to this being somewhat tested) to hold all types of check data.
            * Access: Generic fetching method and getGenericInstanceRegistry() for PlayerData.
            * Add a DefaultCheckData object with  getXYZData methods relaying to IHandleS for efficient access of default coarse data types. Possibly PlayerData.defaultData().getBlockBreakData().
            * Needs relaying some stuff like ICanHandleTimeRanBackwards to PlayerData with another internal registry thing.
    * Planned fixes:
        * 1.0 high fence (at least evaluate, related to spider / wall climbing).
        * Make FastConsume vs. instant-eat dependent on class/method presence rather than detected Minecraft version.
* Secondary
    * Identify more spots to fix, that don't demand excessive testing/changes.
        * More false positives, such as slime bouncing.
    * Add a registry.log log file, which relays to STATUS only with logging/status.extended set. 
        * This way we can always request the registry.log file, having all sorts of information about which checks and classes are registered at all, and how registry items and event listeners are ordered internally.
        * The output of 'ncp version' will be more compact (only the most often needed stuff inside).
* Tertiary
    * Add a first (rather internal) sketch of auto registry features. RegistrationItem...
        * Trigger with (enable,) reload, plugin enable/disable (class/name) (, and by method call)
        * Further activation conditions (e.g. classes present, arbitrary)
        * Add a ProtocolLib based check for fight.noswing (and possibly other) - use auto registry to enable either the classic or the ProtocolLib based check. IFF, this is about 'packet inversion'.
    * Flags, think of flags.
        * Extend velocity by flags or general RemovalContextS that allow other plugins to control better, when velocity is to be removed or not to be removed - also include notion of delay/latency. Plugins being able to delay removal of entries they themselves add, and/or to ensure friction does work after removal, will help other plugins to use velocity rather than exemption for moving related stuff.
        * RemovalContextS could be made a somewhat general thing to be used with velocity an exemptions and possibly other.

# Scheduled
Topics that will be tackled soon, no guarantee on order.
* Internals
    * Block id removal (~ 1.13): Alter things so NCP will still work.
    * Work towards another type of internal abstraction layer for blocks (shapes, mining, moving, ...).
    * From native access BlockCache to NCPBlock (NMSBlock, ConfigBlock).
    * Include preset shapes (static + dynamic) from config.
* Project structure: Include CompatNoCheatPlus via reflection (?).
* Vehicle envelope: Account for boat speed and acceleration: water/ground/ice (1.12).
* Fight: Detect mobs crammed into narrow space (possibly similar) adapt or skip certain checks.
* Force chunk load: Change to prevent moving within unloaded chunks, adapt data lazily where possible. Use a scheduler-like thing to still load chunks to ensure more smooth operation in average.
* NDT-skip-fly (bow/velocity-optimized).
* Boat placement (1.12 on ground, before on water): deny if ... at least if colliding with other boats.
* Attempt to fix false positives:
    * SurvivalFly: sprint+jump on flat ground (low speed up, bunny condition loss makes use of buffer).
    * SurvivalFly: below micro move threshold issues (0.0625):
        * < 0.025 above ground after respawn (possibly other cases, like stepping to roughly this amount onto layered snow).
        * Jumping onto/around the eye of an ender frame with eye (medium easy to reproduce on 1.11.2).
    * SurvivalFly: piston + slime block push up.
    * SurvivalFly: Move onto block level but not on ground (likely an h-collision with step up ~ layered snow, speed + 0.5 shoes).
    * Stuck in hoppers?
    * Vehicles: piston + slime block push up.
    * Horizontal pushing of pistons.
* Decision for next topic between:
    * Fight checks (multiple iterations pending).
    * Data storage overhaul (multiple iterations pending).
    * set back policy (a) suggest set back (b) new policy: force fall.
* Improve fastbreak to catch bulk breaking of fast-breaking blocks faster.
* Evaluate: hacc with another slightly longer term tracking with extra limit - might allow a lower limit.
* Evaluate: Get rid of horizontal buffer (would yield a lot of reports).
* CreativeFly models, levitation: (Deny) descend speed concept + demand ascend. Make behavior fully dependent on the model (no elytra checking within the check, use some kind of special flag to model ~ glideStyleNoOne idk). Possibly allow glide-style ascend even if deny ascend is set (or ascend speed 0).
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
* NoFall: model lava correctly - cleanup to use extra block flags.

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
* Single conditional action support (might also add generic access to violation levels via those).

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
