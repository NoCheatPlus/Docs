## Build Infos Page - NoCheatPlus 3.16.1 and later.

[Back to the Build-Infos overview.](https://github.com/NoCheatPlus/Docs/wiki/Build-Infos)

----

### 3.16.1-SNAPSHOT-sMD5NET-b1140(cumulative)
* Release type: [BLEEDING] development
* New
    * Support to override block breaking times for specific side conditions: compatibility.blocks.breakingtime
    * Support permission caching (configurable).
* Fixes
    * Improve slime block + piston support (partial).
    * Fix wooden pick with iron blocks (efficiency 0 - 5).
    * Fight.NoSwing: Patch up first attack always triggering.
    * Include soil and grass path in the multi client protocol block shape patch (blind, with lily pad).
    * Attempt to skip Inventory.Open for NPCs in general.
* Internals
    * [BREAKING] Don't allow removal of PlayerData for online players.
    * Other fixes: Disable multi protocol patch with unit tests. Fix Activation return types.
    * [BREAKING] Slight overhaul of check type hierarchy and utilities (No freely definable check types yet.).
    * [BREAKING] Use a new internal event registry, to allow control of processing order, as well as unregistering events.

