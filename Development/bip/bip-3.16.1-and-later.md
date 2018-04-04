## Build Infos Page - NoCheatPlus 3.16.1 and later.

[Back to the Build-Infos overview.](https://github.com/NoCheatPlus/Docs/wiki/Build-Infos)

----

### 3.16.1-SNAPSHOT-sMD5NET-b1144(cumulative)
* Release type: [BLEEDING] development
* New
    * The void-to-void set back policy now supports dragging players downwards into the void.
    * Support for overriding block breaking times for specific side conditions: compatibility.blocks.breakingtime
    * Support permission caching (configurable).
    * Fight.WrongTurn: Invalid pitch (experimental).
    * SurvivalFly: Don't allow relaxing the VL in-air (configurable), neither allow horizontal buffer regain, if frozen.
* Configuration
    * Activation (_active_), lag adaption (_lag_) and _debug_ flags: starting from _checks_ for all sub checks, the value 'default' now means checking the check/group above in the hierarchy, enabling you to turn on/off activation/lag-adaption/debug for groups of checks with one switch. Note that not all _active_ flags are actual checks with a check type (yet), best compare to the default configuration, where _default_ is set.
* Fixes
    * Fix dealing too high amounts of damage with jump effect.
    * Fix passable with fences at 1.0 height.
    * Adjust lost-ground case to accommodate for equipped end portal frames.
    * Improve slime block + piston support (partial).
    * Fix wooden pick with iron blocks (efficiency 0 - 5).
    * Fight.NoSwing: Patch up first attack always triggering.
    * Include soil and grass path in the multi client protocol block shape patch (blind, with lily pad).
    * Attempt to skip Inventory.Open for NPCs in general.
    * Define all the default child permissions within plugin.yml (check .silent, command filter).
* Incompatible
    * MC 1.6.x and older: Old versions of ProtocolLib might be incompatible (Temporary players vs. getUniqueId).
* Internals
    * [BREAKING] Don't allow removal of PlayerData for online players.
    * Other fixes: Disable multi protocol patch with unit tests. Fix Activation return types.
    * [BREAKING] Slight overhaul of check type hierarchy and utilities (No freely definable check types yet.).
    * [BREAKING] Use a new internal event registry, to allow control of processing order, as well as unregistering events.
    * [BREAKING] Always use permission subscriptions for notifications. Might lead to notifications missing, if a permission plugin somehow bypasses the subscription mechanics. Removes PermStateReceiver and related internals.
    * [BREAKING] New implementation of exemption handling (basic internals: consistency within thread-context, thread-safe access, mimic legacy behavior).
    * [BREAKING] (I)WorldDataManager stores all sorts of per-world (-per-check-type) things (to be continued).
    * [BREAKING] (I)PlayerDataManager stores per player data (including config cache, debug flags, exemptions).
    * [BREAKING] (I)PlayerData holds a cache for per player configuration and data.
    * (Other cleanup, fixes related to the more complex recent additions.)
