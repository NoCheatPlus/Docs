## Build Infos Page - NoCheatPlus 3.13.6 _**and earlier**_.

**These builds are outdated.**

[Back to the Build-Infos overview.](https://github.com/NoCheatPlus/Docs/wiki/Build-Infos)

----

### 3.13.6-BETA-sMD5NET-b924(cumulative)
* BETA release (bug fix release).
    * MD5: 1304836258112f28f274f2716256498a
    * SHA512: 68af0db1e76c94725b96cb320125fc322641e5543d0c4fb51a9f8827c71f19fda4cabf929168d4b73a7a421cc45f22e7701b65f629851ba827a2109a99430678
    * File size: 1032503
* Fixes
    * Detect if the head is hitting the ceiling in a more reliable way.
    * Adjustments for low ceilings.
    * Stepping onto boats.
    * Fly -> no fly: Fix several false positives (fall damage and speed).
    * Reduce false positives with blockinteract.visible (ProtocolLib, experimental).
    * Confine use of certain workarounds further (more to follow).
    * For GitHub: Change version to use '~' instead of '(' and ')'.
* Internals
    * Add a framework for workaround confinement.
    * Optimize/Simplify random parts of SurvivalFly.
    * Log improper API access with more details.
    * Log "untracked" outgoing position.
    * Allow hooks to test if anything would be logged in a convenient way.
    * More consistent debug log message format.
    * Prepare changes to data storage handling.

### 3.13.5-BETA-sMD5NET-b914(cumulative)
* BETA release (bug fix release).
    * MD5: 23ae92274bd28b947cabbf9cade76823
    * SHA512: 781375ccaa43b48faf87a0bcaca3eed7d2936e63879c7756ea50b38e9b3290cc5690fc68a45a78f30cbf00d487f560019e0a9ae321fe919eeafe7fd22a77aaab
    * File size: 1006298
* Fixes
    * Fix selected issues with sprint-jumping and a 2-high ceiling.
    * Workaround slowness + sprint + jump (not confined to jumping yet).
    * Higher jump effect: ground -> ground.
    * Various other cases for SurvivalFly with vdistrel, swimdown, swimup, mostly with velocity.
    * Fix vdistrel after data reset (and other related).
    * Slime + carpet.
    * Don't allow using items on blockinteract.speed violations.
* Other changes
    * Exempt players by metadata 'nocheat.exempt' (wildcard).
    * Add related plugins versions to the output of '/ncp version'.
    * Confine 'step' detection.
* Internals
    * Rework past move data keeping (lots of impact).
    * Adjust several thresholds for bunny hopping.
    * More robust teleport handling.
    * Move some static code to a Magic class.
    * Pull request 37.


### 3.13.4-BETA-sMD5NET-b901(cumulative)
* BETA release (bug fix release).
    * MD5: 38ae82e1374e5c965460cec2ced93f48
    * SHA512: f49ebc1037b8b09f35dd9c5ebf246a58f4a67ef1c60d3a9225ba124bf6c44853541b3853ed60edb0d32481829c86ce5d0b9275f534844121b50f264a6e04f0df
    * File size: 999748
* Fixes
    * More edge cases for survivalfly/liquid.
    * Special case for a set-back loop with teleport to in-air (PaperSpigot 1.7.10).
    * Detect teleport ACK better, potentially reduces false positives with FlyingFrequency.

### 3.13.3-BETA-sMD5NET-b895(cumulative)
* BETA release (bug fix release).
    * MD5: 79364b259d35a19904ec69d29f6e817c
    * SHA512: 8440feda6944a98f635121276450eddf439ba1c83212ed07858b4aff1114e706cce1b2102e58e45a0fc72bec514a1738a268002c38a43c70d39995e2d0188c19
    * File size: 996682
* Fixes
    * Allow ProtocolLib 3.6.4 for all supported versions of Minecraft.
    * Fix extreme speeding.
    * Fix moving on ENDER_PORTAL_FRAME.
    * Fix jumping on fence with water above. Special case for falling fast into water.
    * Disable the stance checking for 1.8 and later.
    * Fix legacy compatibility (THORNS, PacketFlying interpretation for 1.7.10 and before, disable net.attackfrequency on 1.6.4 and before, allviolations hook).
* Other changes
    * Let the allviolations hook log for players who have debug set (thus shows up by default).
    * Only skip net.flyingfrequency on ACK, don't cancel "stray" packets (potential cross-plugin issues, freezing).
    * Remove (some) deprecated configuration.
* Internals
    * API change: move some things from ServerVersion to GenericVersion.
    * Set more internal Maven dependencies to 'provided' scope.
    * Random fixes (LinkedCoordHashMap).

### 3.13.1-BETA-sMD5NET-b883(cumulative)
* Bug fix BETA release. Prefer this one over the last one (build 878).
    * MD5: e726c6faa32d5d8fbd80b46306cdb57d
    * SHA512: 6efa148a81a02a7f419ee2fed26a9cbfb5ac2c211b6321150b175476fd0ad39aa5eb87d9dbbc949bb56c2a2781a16030b012f0b058b27dd798caebf6bf70a8ba
    * File size: 984969
* Fixes
    * Fix logging backend activation flags being ignored.
    * ProtocolLib: Build against the current version. Only enable for 1.8.x.
* Internals
    * API change: ActionFrequency and ActionAccumulator moved to a sub-package.
    * Use scope 'provided' for all external dependencies.

### 3.13.0-BETA-sMD5NET-b878(cumulative)
* BETA release for 1.8.x.
    * MD5: e064ed398b8034c1ae4b2b699aceb17b
    * SHA512: 1682ab66e33327a263b39f2962be554be46d4efaea2cfda0d534d4d36068432d2473c713b6605705e445e1fccfeff152ea0f0fad9fcc876462577ac38763a9b5
    * File size: 980163 bytes
* BUGS:
    * ProtocolLib incompatibilities.
    * Logging backend activation flags ignored.
* Hot
    * 1.8.x support.
    * Reworked y-axis handling.
    * With ProtocolLib: net.attackfrequency (compensates for the inoperable fight.speed).
    * Add ability to skip captcha for commands.
* Fixes
    * Indirect fixes by stricter y-axis handling (use-velocity-once, friction, pretty strict envelopes). Fast fall, glide-by-velocity, other.
    * Farmland block shape.
    * Prefixes are moved to loggers (ensured them to work).
    * Consistency fixes (e.g. when depth strider applies, when all speed modifiers apply).
    * Reduce false positives with creativefly (fly speed upwards, transition to survivalfly).
    * Reduce false positives with passable.
    * Reduce false positives with survivalfly (though different new ones might have been added).
* Removed
    * Remove cancelling redundant packets for now.
    * Prefix for console no longer available.
* Internals
    * Optimizations for asynchronous logging/stats.
    * Moving checks: split checking into two moves when confronted with micro moves.
    * Various optimizations and consistency fixes, preparations for future changes.

### 3.12.1-SNAPSHOT-sMD5NET-b853("mostly stable", cumulative)
* Recommended release for "classic" y-axis handling.
* Hot
    * 1.8.x support.
    * Many fixes, changes, optimizations, deoptimizations.
    * Represents the last build with the "classic" y-axis handling, having removed a lot of false positives.
* Big issues.
    * Vulnerable to glide-by-velocity.
    * The fight.speed check is mostly inoperable on 1.7.10/1.8.x.


### 3.12.0-BETA2-sASO-b813(cumulative)
* Planned beta release on BukkitDev (not built on Jenkins!).
* New
    * MC 1.8.3 compatibility [BLIND].
* Changes
    * Autosign: Allow to ignore empty signs.
* Fixes
    * Fixes for ray-tracing in general (moving.passable + blockinteract.visible)
* Internals
    * Rework ray-tracing base. Add more automatic testing.

### 3.12.0-SNAPSHOT-sMD5NET-b804(cumulative)
* New
    * [Net] Keepalivefrequency: Prevent spamming, improve Godmode.
* Fixes
    * Critical fix for testing for exemption.
    * Ensure packet level checks can process asynchronous packets.
    * Reduce false positives with survivalfly and ray-tracing (passable).
    * Prevent abusing NoFall to accumulate velocity too easily.
    * Fixes for Fight.Direction.
    * Fix issue with logging on disabling the plugin.
    * Version detection fixes.
* Other Changes
    * Creativefly uses per-game-mode settings now.
    * Fight.Godmode: use data from ProtocolLib hooks too.
    * Alter debug logging output/config.
* Internals
    * Removed some deprecated methods and interfaces (!).
    * Various: cleanup, refactor, simplify.

### 3.12.0-SNAPSHOT-sMD5NET-b793(cumulative)
* New
    * FlyingFrequency (ProtocolLib) Cancel redundant packets.
* Fixes/Changes
    *  Extend configuration for packet level checks, optimize.

### 3.12.0-SNAPSHOT-sMD5NET-b791("mostly stable", cumulative)
* New
    * Passable: Monitor commands and teleportation by commands (correct or cancel, if untracked). Might need configuration for commands.
    * Gutenberg: Prevent creating books with more than 50 pages.
* Fixes/Changes
    * Re-adjust block break timings for melons and pumpkins.
    * SurvivalFly: Skip some checking if players are not moving any distance.
    * SurvivalFly: Fix knockback, low jump detection, a bunny weakness.
    * Fix breaking ore blocks with pickaxes.
    * Fix putting mob eggs on item frames.
    * Command protection: Make trailing spaces work, catch "x:y" commands even with simple configuration ("y").
    * Spectator game mode: allow passing through blocks.
    * Enable/disable some features depending on the Minecraft version (knock-back-velocity, enforcing locations).
    * Extend the "ncp version" command to show some of the available features.
    * Log file: allow "" and "none" to not use any, prevent failure with invalid naming.
    *  Extend configuration for packet level checks, optimize.
* Removed
    * Removed the knockback (fight) check.
* Internals
    * Alter exemption-API and accessibility.

### 3.12.0-SNAPSHOT-sMD5NET-b776("mostly stable", cumulative)
* Hot
    * Basic native support for 1.8/Spigot. (Attempted to fix: fences/gates, depth strider, flying, melons, pvp-knock-back, jumping on slime blocks.)
* New
    * Block codes for JourneyMap caves and rader (covers VoxelMap too).
    * Per player debug tracing (rudimentary, remove data to turn off).
* Fixes
    * Logging: Interpret log file as a folder, if no extension is given.
    * Fix NullPointerException with the command protection feature.
    * Fix NullPointerExcetption with packet checks (moving). 
* Internals
    * Preparations (fight:location-trace).

### 3.11.2-SNAPSHOT-sMD5NET-b763(cumulative)
* New
    * Logging has been reworked. 
        * File logging is now done asynchronously and always contains what NCP logs to console for initialization and shutdown. Absolute path names can be used now.
        * Specify an existing directory to get log files named by date and sequence (e.g. create and use 'logs' in the plugin folder).
        * Most logging is now done asynchronously (file, console). Ingame notifications are still sent directly from the primary thread.
        * Work in progress: Options to control features, balance prefixes, subject to feedback.
* Fixes
    * Attempt to sharpen fight.criticals.
* Internals
    * Dedicated module for CB 1.7.10 (MC 1.7.10).
    * Catch and log exceptions, if loading chunks fails.
    * Configuration is now loaded early in onLoad.
    * Internal logging API has been changed.
    * Optimizations, refactoring, code formatting.

### 3.11.2-SNAPSHOT-sMD5NET-b754("mostly stable", cumulative)
* New
    * Add block properties for MC 1.8 [effects by slime blocks are not yet supported].
    * Experimental Glowstone (server mod) support. Few tweaks on top of MCAccessBukkit (like bukkitapionly mode).
* Config/strings: Add name and displayname for players.
* Other changes
    * Not set log/strings paramters are shown with [...] once more.
    * Passable: Add locations and distance to logging.
    * Log logout location, if debug is set.
* Fixes
    * FastBreak: Update timings for obsidian.
    * CreativeFly: Don't allow to go above maximum height with velocity.
    * Passable:
        * Fixes for set-back selection.
        * Detect players having moved into a block just before logout ina sneaky way, set-back if feasible.
    * CompatBukkit: Implement correct widths for entities (up to 1.7.10).
    * Packet checks: Actually allow enabling/disabling on a per-world basis.
    * Fix optimization of log actions.
    * Fix methods used in test-cases (manhattan).
* Internals
    * Various: Code formatting, optimizations (e.g. TickTask), simplifications.
    * Preparations (frozen) for changing vertical velocity handling.

### 3.11.1-RC-sMD5NET-b743(**release**)
* **Release on BukkitDev.**

### 3.11.1-SNAPSHOT-sMD5NET-b742(cumulative)
* Changes
    * Passable raytracing: Removed the vcliponly option, set blockchangeonly to false by default, extend "early exit" check.
    * "ncp inspect": Added op status to message.
* Fixes
    * Raytracing/Passable: Prevent moving through diagonally closing blocks.
    * Fix a NullPointerException with command protection.
    * Only log certain debug messages if logging.debug is set.
* Internals
    * Refactor parts of velocity handling to prepare for per-axis velocity.
    * Passable raytracing: Added unit tests.

### 3.11.0-RC-sMD5NET-b739(**release**)
* **Release on BukkitDev.**

### 3.11.0-SNAPSHOT-sMD5NET-b738(cumulative)
* Hot
    * CraftBukkit for Minecraft 1.7.10 support.
    * Packet level checks, currently depending on ProtocolLib:
        * Flying packet spam prevention (magnet/repell, healing).
        * Sound distance (some sounds can reveal players whereabouts).
    * "ncp top" command to search violation history for top violations.
* Other news or important changes.
    * The moving.morepackets check has been rewritten (vehicles are left untouched for the moment).
    * The speeding permission (survivalfly) now affects all horizontal speeds, including swimming and web.
    * The "inspect" command now includes the game mode of the player.
    * Add or start adding "log" and "reset" commands, stating some statistics for debugging purposes, e.g. silent cancelling.
    * Renamed tempkick to denylogin, unkick to allowlogin, and kicklist to denylist (aliases should make it compatible).
    * The most "dangerous" auxiliary (action-) commands can only be run from the console from now on.
* Fixes
    * MILK_BUCKET with fastconsume.
    * Do make use of child permissions of nocheatplus.checks.blockplace.against.
    * Prevent combined.bedleave kicking, if you reload NCP with a plugin manager.
    * Fix kicking behavior on "illegal moves".
    * Abort ray-tracing if there is no advance.
    * Internal position resetting on moving set-backs.
    * Ensure ActionFrequency resets with time running backwards. Affects many checks (relevance: rare to never for most servers).
* Internals
    * Make ConfigManager.getConfig(...) available from all threads (copy on write, pitfall: altering the config during runtime is problematic now).
    * New generic registry for general purpose instances, providing "Counters" for counting things, displayed with the "ncp log counters" command.
    * Minor cleanups (unused API, commands, renames, indentation/random).

### 3.10.13-SNAPSHOT-sMD5NET-b704(cumulative)
* New
    * Prevent dead players from doing some things, e.g. interacting, eating. Not all inclusive, yet.
    * (Old:) Add back a compatibility tweak for instant breaking of blocks, used by other plugins.
* Fixes
    * Prevent bypassing inventory.instantbow with invalidating interaction timing.
    * Fix a test failure for building the plugin. 
* Internals
    * Use the vanilla ban command for "ncp ban", warn on using uuids.
    * Concentrate block-id use to few places.

### 3.10.12-RC-sMD5NET-b700(**release**)
* Release on BukkitDev.

### 3.10.12-SNAPSHOT-sMD5NET-b699(cumulative)
* New
    * Allow disabling chat.text violation level reset. This might be subject to further changes in the near future.
* Fixes
    * Fix instantbow bypass.
    * Fix raytracing safeguard not being initialized correctly for some cases.
    * Add an exception list for blockplace.noswing (default to water lily + flint and steel).
* Config changes
    * Slightly increase default delay setting for fastbreak.
* Removed
    * Direction correction feature.
* Internals
    * More safeguards against accidental misuse of temporary Location objects.

### 3.10.11-BETA-sMD5NET-b690(**beta release**)
* Beta release.

### 3.10.11-SNAPSHOT-sMD5NET-b689(cumulative)
* Fixes
    * Fix moving events while in vehicles. 
* Internals
    * Treat respawn mostly like join. Both the hover and enforcelocation features could now kick in. [Unresolved: Some worlds have the spawn location set underground, but spawn the players above - currently this is conflicting, you should use a simple plugin to set the world spawn manually in such a case.]
    * Apply yaw/pitch correction directly in fight-handling. [Likely inoperable, might get removed, simply.]

### 3.10.10-BETA-sMD5NET-b686(--beta release--)
* //DEFICIENT: Issues with vehicles.//
* --Beta release.--

### 3.10.10-SNAPSHOT-sMD5NET-b685(cumulative)
* //DEFICIENT: Issues with vehicles.//
* New
    * Dedicated MC 1.7.8 / 1.7.9 Support
    * The parameter [uuid] can now be used in the strings section of the configuration.
    * Experimental yaw+pitch correction.
* Fixes/Internals
    * Blockplace.fastplace: The violation level will increase a thousand times faster now.
    * Review of command protection features.
    * Warning messages for MCAccess have been reviewed.
    * Added more safety guards.

### 3.10.10-SNAPSHOT-sMD5NET-b676("mostly stable", cumulative)
* New
    * Dedicated MC 1.7.5 Support
    * fight.reach and fight.direction have been altered.\\Work in progress: In future they will allow hits to register for situations with a lot of latency. Currently only the latest location and those that arrived in the same tick are counted in, also the checking logics is the same as before, for the sake of finding bugs without altering too much at once.
* Fixes
    * NoFall: Ignore players in vehicles when they take fall-damage. Aims at issues with horses.
    * NoFall: Potential fix for issues with players that are allowed to fly or in creative mode on logout.
* Internals
    * Maintain a trace of past locations for players. Aiming at fight-checks.

----

### 3.10.9-RC-sMD5NET-b673(**release**)
* Release on BukkitDev.

### 3.10.9-SNAPSHOT-sMD5NET-b672(cumulative)
* Hot topic
    * Dropped compatibility with CB before 1.4.5-R1.0!
* New
    * Check location consistency, counters some new vclip/tp exploits. Silent set-backs, config: checks.moving.enforcelocation
* Configuration
    * The message for console-only commands is now configurable.
    * Set checks.moving.assumesprint to true by default, to avoid a lot of false positives.
* Fixes
    * WrongBlock should not generate extreme violation levels anymore.
    * Still process captcha for cancelled chat events, e.g. with players muted by another plugin.
    * Confine conditions for survivalfly/sprintback further to avoid false positives.
    * Fix block shape issue with stained glass panes.
* Internals
    * More efficient location handling (less object creation).
    * Various cleanups (set-back handling, safety guards, code formatting)

### 3.10.8-RC-sMD5NET-b664(**release**)
* Release on BukkitDev.

### 3.10.8-SNAPSHOT-sMD5NET-b663(cumulative)
* Fixes
    * Avoid sign duplication due to a bug in CraftBukkit.
    * Fix moving on ender portal frames with eyes on.
    * Adjust to work with latest CB and other 1.7.2 beta builds.
* New features
    * Ctrl+sprint: Add a workaround option to let NCP assume a player is sprinting, whenever possible (checks.moving.assumesprint).
    * Changing the tool now leads to a configurable attack penalty (checks.fight.toolchangepenalty).
    * Changing the tool now resets the block-break timing.
    * blockplace.against is a "full check" now - previously without history entries and without configuration.
* Configuration changes
    * checks.fight.direction is now set to false by default.
    * Increased the default kick-level for the moving.survivalfly actions to 1500.
    * checks.moving.passable.raytracing.vcliponly is now set to false. This means much more checking but prevents moving through walls exactly horizontally by default.
    * Increase the fall distance for which the critical check can trigger. Now a moving event is forced, if a cheat-client wants to go just above this distance.
* Random
    * Review sprint-handling.
    * Review penalty time handling.
    * Allow removal of fight.selfhit data without removing all fight data.

### 3.10.8-SNAPSHOT-sMD5NET-b655 ("mostly stable", cumulative)
* Fixes
    * Fix breaking time for Acacia leaves + shears and similar.
* Random
    * Close inventory on players leaving.
    * Log if 1.7.2 blocks are added.
    
### 3.10.7-BETA-sMD5NET-b651 (**release**)
* Beta release on BukkitDev.

### 3.10.7-SNAPSHOT-sMD5NET-b650 (cumulative)
* New
    * Rough update to MC 1.7.2.
* Changes:
    * Log "system time ran backwards" on warning level.
    * Removed some deprecated internal API.

### 3.10.6-RC-sMD5NET-b644 (**release**)
* Release on BukkitDev.

### 3.10.6-SNAPSHOT-sMD5NET-b643 (cumulative)
* Fixes
    * Vehicles: Attempt to confine the player to the vehicles location (roughly).
    * Vehicles: Adjust set-back handling + prevent destroying ones own vehicle.
    * Passable: Attempt to harden set-back handling against certain exploits.
    * SurvivalFly: Attempt to fix a false positive with sprint+jump.
    * SurvivalFly: Fix and simplify vertical accounting.
    * Fight: Part-fix issues with TNT. Problems might remain with the death of the engineer.

### 3.10.5-RC-sMD5NET-b633(**release**)
* Release on BukkitDev.

### 3.10.5-SNAPSHOT-sMD5NET-b632(cumulative)
* Configuration changes (only needs updating the spots mentioned below):
    * Add missing cancel action for fight.fastheal.
* Internals
    * fight.fastheal: Include a case with too much health, somewhere.

### 3.10.4-RC-sMD5NET-b631(**release**)
* Release on BukkitDev.

### 3.10.4-SNAPSHOT-sMD5NET-b630(cumulative)
* MC/CB 1.6.4 support.
* General Changes
    * Removed metrics. Might get re-added once certain which services to use.
* Configuration Changes
    * The inventory closing is moved to its own check (no violations triggered), allowing to track some fighting cheats better. No changes for processing yet, just preparations.
* Internals
    * Add Listeners for plugin-disable, use for some cleanup of internally used static members.

### 3.10.3-RC-sMD5NET-b626(**release**)
* Release.

### 3.10.3-SNAPSHOT-sMD5NET-b625(cumulative)
* Fixes:
    * Fix creativefly allowing small horizontal moves to equal out too far vertical moves.
    * Fixes for shortcut permissions in the plugin.yml.
* Log messages:
    * Let metrics fail silently unless logging.debug is set.
    * Start and end of "post-enable" is now logged.

### 3.10.2-RC-sMD5NET-b620(**release**)
* Release on BukkitDev.

### 3.10.2-SNAPSHOT-sMD5NET-b619(cumulative)
* New
    * New shortcut permissions.
    * Command "ncp inspect (player)": info about health, walkspeed and similar.
* Configuration changes
    * opinconsoleonly: Add a commands list for more general use, put into protection.commands.consoleonly section.
    * All command lists in the configuration can be set up without using the prefix "/".
    * Plugin hiding: Individual sections for "unknown command" and "no permission", adding lists of commands to change.
    * The managelisteners options has been moved to the compatibility section.
* Permission changes
    * Backwards compatible: New shortcut permissions, commands are grouped under nocheatplus.command (.admin still works, child nodes will be kept compatible for a while).
    * Permissions for notifications are now split into nocheatplus.command.notify and nocheatplus.notify. 
* Fixes
    * SurvivalFly: Fix vertical accounting letting a variation of "glide" slip through. Further reduce false positives (lost bunny).
    * Nofall: Fix fractional damage for too low fall distances. Attempt to fix issues with horses.
    * Passable: fixes for ray-tracing (incl. alse postives).
    * Fixes with inventory closing.
    * BukkitCompat: Keep command protection operable (get the command map by reflection).
* Internals
    * Chat processing also attempts to test the original command label (consoleonly, handleaschat, exclusions).
    * Command/plugin hiding now is done via permissions and permission-message for the commands, not parsing commands.
    * The filter permissions for commands are now grouped under nocheatplus.filter.command.

### 3.10.1-beta-sMD5NET-b601(beta release)
* **//Beta// release on BukkitDev.**

### 3.10.1-SNAPSHOT-sMD5NET-b600(cumulative)
* Hot
    * Change version naming, adding "series" hinting at build server/purpose.
* Configuration Changes
    * Default SurvivalFly actions: Longer delay for low-vl log messages.
* Fixes
    * Moving: Fix sprinting time not resetting. (Once the client tells not to be sprinting, we don't need to care for latency anymore.)
    * SurvivalFly: Attempt to catch "glide" with vertical accounting [Could cause new false positives, NEED FEEDBACK].
    * SurvivalFly: The workaround for sprint/bunny while attacking others is modeled differently, which should now work with sprint effects.
    * SurvivalFly: Prevent negative horizontal buffer.
    * CreativeFly: Jump amplifier gets reset properly now.
    * Waterwalk: Fix waterwalk triggering for walking into water on some occasions.
    * Worked around in earlier builds: carpets.
* API extensions:
    * Configuration handling: Action factories are set up lazily now in order to allow better overriding by other plugins. Effect could be that once per reload some events get a higher processing time (only the first getting of the config).
    * INotifyReload can be registered with a priority set in an annotation, thus you can ensure your reload hook gets called before any NCP-internal hooks.
    * LogAction: Constructor used for optimized action is now on protected visibility instead of private.
* Internals
    * SurvivalFly: Cleanups: Move some code into methods, alter checking order in some places, comments, other.
    * SurvivalFly: Revert allowing to consume buffers and velocity for sprintback, change extra buffer to counter for the "lost sprint" problem.
    * SurvivalFly: Reduce reference-sprinting-speed by changing the "bunny hop" modeling (hop + fly phase, compensate with buffer).
    * SurvivalFly: Perform less double checking (perm checks) by testing bunny first, and a second time afterwards only if necessary.
    * SurvivalFly: Bunny-hop: Also applies when not sprinting, also with not jumping. (Working towards confining/removing the buffer.)

### 3.10.1-SNAPSHOT-b587(cumulative)
* Hot
    * Account for per-player walk-speed and fly-speed.
* Fixes
    * Skip survivalfly for flying players (...). Previously only players that were allowed to toggle fly were exempted from sf.
    * Part-fix issues with throwing ender pearls at nearby cows and players, triggering survivalfly with limitjump.
    * Attempt to fix sprintback issues with horizontal velocity.
* Internals
    * BridgeHealth: attempt to improve compatibility with special player classes as used by Essentials.
    * Alter/extend debug output (misc.).
    * Cleanups (vehicle handling, comments, javadocs).

### 3.10.1-SNAPSHOT-b580(cumulative)
* Changes:
    * Configuration version: Now has its own section in the configuration, notification can be disabled.
    * Configuration outdated warnings and notify-off message are sent delayed, not from within PlayerJoinEvent-handling.
    * Health-API incompatibility warnings: Only show if logging.debug is set.
* Fixes
    * Passable: Fence gates, moving out of blocks if stuck (tp, login), creativefly ignoring passable set-back, vcliponly covers up and down now.
    * SurvivalFly: Web + stairs/steps.
* Internals
    * Moving debug output will contain walkspeed + flyspeed (future use).
    * Passable: Potentially improve performance by an earlier return for moves that are fully inside of ignored blocks.
    * More cleanup for health-API changes.
    * Event priorities for some core setup changed (world change + player join set to low), affects mod message sending.
    * Added global message-sending queue preserving registration-order (currently thread-safe). Used for delayed sending of notification messages and warnings for chat.txt.

----

### 3.10.0-RC-b569(**release**)
* **Released on BukkitDev.**
* Hot
    * MC/CB 1.6.2 Support.
* fixes
    * Metrics: Do start/cancel metrics on reloading as well, not only on startup.
* Internals
    * More complete support for the health changes with 1.6.
    * Core dependency set to 1.6.2, so older versions suffer some slower compatibility methods rather.
    * Alter checking order for some fighting checks.
    * Minor cleanups.

### 3.9.4-DEV-b558("mostly stable", cumulative)
* Hot
    * MC/CB 1.6.1 Support.
    * Few config paths got changed, old settings are preserved.
* New
    * Make messages configurable for hiding plugins (unknown command, permission message), with color.
    * It is now possible to completely deactivate motd sending for client mods.
    * Added hook versions to the output of "ncp info".
    * Just in case: To keep the morepackets-vehicle check effective, auto-detection of vehicle events has been added. [Should work, missing: use new events for mount/dismount etc.]
    * Just in case: Force close inventories on portal use and world changes, also taking into account riding on entities (on entities...).
* Fixes
    * Workarounds added for potential problems with other plugins that don't implement certain compatibility tweaks for the changes in Bukkit from MC 1.5.2 to 1.6.1.
* Internals
    * Updated metrics to R7.
    * Make use of Material.hasGravity for CompatCBDev.
    * Optimize color handling.

----

### 3.9.3-RC-b539(**release**)
* Release on BukkitDev.

### 3.9.3-DEV-b538(cumulative)
* New
    * Add command to turn in-game notifications on and off, per player:\\// /ncp notify on|off//
    * Change logging configuration to sub-sections (automatically changes config).
    * Make prefixes for log messages configurable.
    * Add option to suppress inconsistency warnings for DataMan + players.
* Fixes
    * Fix memory leaks with unloaded worlds.
    * Attempt to fix issues with interact.visible by checking alternate positions as well.
    * Update inventory after fastconsume violations (fixes items but not hunger bar).
    * Fix compatibility issue with vehicles and BKCommonLib (adds: nofall.resetonvehicle).
    * Fix random damage with nofall.dealdamage set to false (not recommended to use anyway, unless really necessary).
    * Fix survivalfly triggering with the "step" tag for jumping onto/alongside a one block high thing with higher jump effects.
    * Add missing permission to plugin.yml: fastconsume
* Internal changes
    * Add moving (renaming) config paths and deprecated config paths as concepts.
    * PlayerData can carry arbitrary tags now.
    * Rework commands for easier sub-command adding.
    * Add a filter permission to use any command at all. There should be no need to add it, because it is set as child permission of all sub-command permissions.

----

### 3.9.2-RC-b520(**release**)
* Release on BukkitDev.
* Add FastConsume check for consuming items (replaces instanteat).
* Fix loading wrong chunks on join/hover checks.
* Few fixes for fastbreak (cocoa / vines, iron/gold blocks)
* Add concept to moving checks: allow sprinting for while even after food level dropped too low. Attempts to reduce false positives.
* Attempt to reduce problems with inventory features (shift+ double click with item in hand).
* Internal changes (some API methods are non-static now).
* Adjust some debug output for nofall/moving.

----

### 3.9.1-RC2-b510(**release**)
* Release on BukkitDev.
* Add another default flag to steps (xz100).
* Comment out dead code to make sure BukkitDev staff does not stumble over it.

### 3.9.1-RC-b509(planned release)
* Planned release for BukkitDev: rejected.

### 3.9.1-RC-b508(cumulative)
* 1.5.2 Support.
* Add checks against ender-pearl abuse (no permission for this, yet).
* Add autosign check.
* Fix crop trampling being disabled by anti-criticals (add low-jump detection).
* Fix issues with standing on stairs.
* Load chunks where players join.
* Attempt to fix issues with taking fall damage for falling while not having received chunks (part-fix).
* Fix block breaking times for being in lava and similar.
* Permissions setup updated (plugin.yml).
* Internals rework for client mod motd-messages.

### 3.9.1-RC-b495("mostly stable", cumulative)
* Fixes for moving checks and player-join (npe).
* Hover: force load chunks before re-checking on-ground.
* Login-denial is configurable for illegal-move checking.
* Less strict default settings for chat.logins.
* Fix breaking time for "locked chest".
* Consistency fixes and extensions (fixes some chat checks data not resetting with the remove command).

----

### 3.9.0-RC-b488(**release**)
* Release on BukkitDev.

### 3.9.0-b486(cumulative)
* MC 1.5.1 and 1.5.0 support (blocks + obc/nms-access).\\//This allows players to move into corners of fence-setups also for earlier Minecraft versions.//
* Add basic thorns support (workaround for missing API).
* Fixes for fastbreak with wood-pick + efficiency.
* Might have given jumping on boats slightly more tolerance.
* Consistency fixes (block setup, prevent CB2511 module loading for libigot/no-safeguard-mods).

----

### 3.8.12-RC2-b472(**release**)
* Release on BukkitDev. [Last minute fixes might follow.]
* Catch on case for ArrayIndexOutOfBounds with InventoryClickEvent.

### 3.8.12-RC-b471(planned release)
* Planned release.

### 3.8.12-b470(cumulative)
* Re-code inventory.fastclick. Likely it is more forgiving on first glance and we might need to add specialized tool/weapon/food checks later, however it allows better control over limits, rudimentary support for some 1.5 inventory issues/features.
* Fix passable ray-tracing not respecting the block-flags.
* Add an example entry for overriding block-flags (doing nothing). Snow levels might not work on 1.4.7 servers with hackish 1.5-protocol support, which can be part-fixed by setting the flags for snow to ground+solid+height_8_inc.

### 3.8.11-RC-b467(**release**)
* Release on BukkitDev. 

### 3.8.11-b466(cumulative)
* Add "blind" MC 1.5 block support. This is an attempt to make 1.5 playable with the bukkit-api-only compatibility module in use. Block breaking times are not adjusted, but the blocks are initialized with some flags for moving over them etc. If a block poses a problem flags can still be overridden using the configuration of NCP.
* Add "ncp unkick *" option to remove all players from the deny-login list.
* Fight.reach distances (survival) are configurable now.
* Add "default" flag option for overriding block flags, for conveniently adding few flags without having to guess the others. More tolerant flag parsing (whitespace), allow '+' for flag-separation as well.
* Consistency fixes for data removal (affects chat.logins for instance).
* Fix godmode being checked for dead players.
* Fix for survivalfly/swimup and stairs.
* Fix "downstream" judgment for horizontal speed not taken into account on second check (after failure).
* Horizontal veloctiy handling:
    * Fix wrong counter being used once activated.
    * Add maximum tick age for activation. This prevents waiting for a long time without moving before using velocity.
* Use of more exact bounding boxes for the player (mainly survivalfly).
    * Reduced the number of blocks visited and deeper checking.
    * Various changes to workarounds and other. Could reduce some false positives, could also create new.
    * Fixes falling through narrow spots and taking fall damage on some occasions.
* General fixes to block collision logic. Includes changing some flags and workarounds.
* Fixes for block flags with "bukkit-api-only".
* Fixes for MCAccess modules (data cleanup, can't stand on minecarts)
* More performance related changes (moving/survivalfly).
    * A little less object creation.
    * Re-group some checking and distribute to several methods.
    * Collect flags for a smaller bounding box.
    * Don't check everything twice if a player does not move.
* Fix: Set the correct potion-effect strength in data.
* Only set velocity flag if velocity is actually being processed (sfDirty).
* Attempt to catch more "lost-ground" cases with block edges.
* Add more detailed tags to lost-ground workarounds (survivalfly) for better debugging.
* Let NoFall look for ground within a slightly extended margin for the case of taking fall damage unexpectedly.

### 3.8.11-b452("mostly stable", cumulative)
* New method of velocity handling for horizontal velocity. The new method uses velocity on demand and allows delayed "activation" to account better for latency.
* Add "strict" option to the fight.direction check. Takes into account not only the distance to the estimated target but also the angle.
* Reduce amount fight.reach can contribute to combined.improbable.
* Fix for non-exact vanilla-respawn.
* Attempt to catch more moved too quickly / moved wrongly teleports in order to prevent resetting of fly-data.
* Further changes and fixes to on-ground judgment.
    * More exact judgement if a player can actually stand on/in a block.
    * Survivalfly workarounds adjusted to catch more fish.
* Consistency: remove some more data on players leaving.
* Performance related changes (mostly moving / on-ground checks).

### 3.8.11-b442(cumulative)
* Changes to on-ground judgement (ongoing), seems consolidated. Aiming at consistency, performance, spiders. [//amining at//, not yet done/finished!]
* Adaption to debugging messages.

----

### 3.8.10-RC-b438(**release**)
* Release on BukkitDev.
* Last minute fix: revert removing shortcut on-ground check, but fix it, instead.

### 3.8.10-RC-b436(planned release)
* Scheduled release on BukkitDev [unless for last-minute fixes.]

### 3.8.10-b435(release phase, cumulative)
* Fixes and more safety guards for ray-tracing (general, passable).
* Reduce false positives with SurvivalFly (jumping onto edges, lost-ground, sprint+jump+attack, sneak/block+velocity, jump+sprint+touch-water).
* Add step option to survivalfly/hover, in order to reduce load by only checking every //step// ticks and a loginticks option to allow giving players a little longer hover time after login.
* Adjust some caching for moving checking and remove a --dubious shortcut-- check.
* Fix zombe/noclip permission flipped.
* Fixes for consistency (data removal for chat data, logins data removal in case of "ncp remove *").
* Ensure some blocks like glass or leaves are not ignored by the passable check for bukkit-api-only.
* Added dev-url.
* Add support for the checks.debug flag, as a possibility to set a preset for all checks debug flags.
* Added build-parameter support.
* Several debug outputs adjusted.
* Adjust and correct messages for MCAccess setup failures/problems.
* Set internal module structure for 1.4.7 in stone, finally.

### 3.8.10-b418 (release phase, cumulative)
* Start of release phase: "mostly stable".

### 3.8.10-ALPHA-b417 (cumulative)
* Add ray-tracing to the passable check.
* Fix passable preventing to jump upwards if stuck but with free head.
* Add blockinteract.speed.
* Add blockinteract.visible (also raytracing for visible blocks, slightly different method).
* Optimize and fix blockinteract checks.
* Add fastheal check.
* Fix direction checks [might need more tweaks against false positives].
* Fixes for survivalfly: standing on sand below cactus, false positives with block edges [not all yet], fix hover check alerting for players who should not get checked after join (flying), false positives with jumping out of water near steps.
* Change configuration of data-expiration: adds an active-flag.
* Add compatibility-option to override any block-flags.
* Add ability to exempt from silent blockplace and blockbreak checks (liquid/air).
* Fix/adjust some messages and preset permissions, debug outputs.
* Fixes for consistency.
* Remove Metrics timeouts (should be ok in an extra thread), since it is more fair to our stats.
* Optimizations.


### 3.8.10-ALPHA-b387 (cumulative)
* Re-code god-mode check [still false positives in b391].
* Survivalfly: change accounting method to something more sharp and less/not influenced by lag.
* Adjustments to velocity-handling. More precise counting + configurable grace-count, invalidate velocity after grace period under certain circumstances.
* Fix for on-ground judgement.
* Fixes for survivalfly: prevent fast moving up water, ladders, etc., reduce some false positives (including cactus), prevent moving on signs.
* Survivalfly: More strict jumping limits also depending on the medium the player jumped from.
* Survivalfly: fall-damage config option added.
* Fix for fastbreak: Higher haste-modifiers.
* Lag adaption for inventory.fastclick.
* All noswing actions were adjusted to not alert for lower levels.
* Adjust some debug messages.
* Bigger internal changes to reduce some dependencies (not affecting normal API use or function).

----

### 3.8.9-b353 (alpha release, cumulative)
* Alpha release on BukkitDev.
* Fix false positives of flying/hover for fences, thin glass and similar.
* Attempt to fix occasional false positives when logging in in water (survivalfly).
* Fixes and performance optimization for the hover check.
* Only add to improbable for normal fighting if target(s) are moving or are apart from each other by a certain distance.
* Attempt to fix backwards-sprinting false positives on survivalfly for the case of taking damage while sprinting+jumping.
* Fix Munchhausen not being enabled ever, even if wanted to.
* Various fixes for internals concerning consistency and cleanup, for instance for reloading the configuration.

### 3.8.9-b344(cumulative)
* Add command "/ncp version" for convenient display of server version, ncp version and MCAccess module in use.
* Fix jumping on boats for a part.
* Attempt to fix issues with exiting boats or boats  being destroyed.
* Fix axes + vines (fastbreak).
* Improve morepackets(vehicle) to actually set back players (also fro pigs) and to only use the earliest set-back in case of many violations within one server tick.
* Fix for dead-people-fighting prevention.
* Fixes for consistency (internal components, TickTask, hover check)
* Fix NoFall bypass - partly revert/renew nofall logic for players receiving fall damage though not being on ground.
* Add more ways to let MCAccess implementations fail (class member checks). Prevents the wrong MCAccess loading for some server mods, future purpose.

### 3.8.9-b335 (cumulative)
* Fixes and "safeguards" for bad inputs for TickTask.getLag and for system time running backwards. Account for the possibility of the TickTask getting reset (not yet a realistic scenario).
* Fix for "bukkitapionly".

### 3.8.9-b329 (cumulative)
* Check morepackets(vehicle) for players riding on pigs.
* Adding compatibility block list to be able to allow "instant breaking" for those blocks, in case a block type poses trouble with fastbreak.
* Add a "bukkit-api-only" compatibility module - it is likely to have all sorts of issues, but prevents complete absence of NCP in case of "accidental updating". [Does have issues, fixes in build 335.]
* Fix for fastbreak: penalty factors for under-water and off-ground.
* Fixes for the hover check (survivalfly).
* Bigger portions of code moved internally + refactoring (preparations for bukkit-api-only support and for future changes).

### 3.8.9-b320### 
* Add fine grained permissions for Rei's Minimap's radar.

### 3.8.9-b319 (cumulative)
* **Support for Minecraft 1.4.7.**
* Fix issue with chat.logins: Already kicked players will not count for logins anymore (checked at priority level "normal", though), specifically players denied to login by NCP itself should not count in anymore.
* Should have fixed issues with fall damage dealt and death-message plugins.

### 3.8.9-b316 (cumulative)
* Add a "hover" check (survivalfly). It might cause trouble with sleeping/dead players on some conditions, but it can be disabled.
* Slight changes to NoFall: Remove "double damage", also having in mind the case of Minecraft dealing false damage.
* Add// /ncp unexempt *//
* Update Metrics.
* Remove old LagMeasureTask in favor of the new TickTask.

### 3.8.9-b312### 
* Fixes for "System time ran backwards". 

### 3.8.9-b311 (cumulative)
* **Seems to have fixed or worked around issues with /spawn and Essentials.**
* Internal changes to keep set-backs "firewalled" against locations coming from outside (//Still not sure what the actual cause was, suspicion is other plugins messing with special objects that behave strangely on cloning and are kept as references somehow, but that is more like an uneducated guess.//). Leads to less object creation from moving checks (unless for set-backs).

### 3.8.8-b310 (cumulative)
* **Incompatibility with Essentials, MultiVerse, MobArena**\\Their spawn locations //seems// to change after some time, does not appear to happen with simple plugins that use the worlds spawn.
* Adjustments to set-backs for moving checks. \\//(See incompatibility note above)//\\Setting the set backs will use less object creation, getting them will create objects rather.
* Add some lag-awareness, i.e. counting in lag durations or skipping short term checks.
* Adjustments to debug output for moving.

----

### 3.8.8-b301 (beta release, cumulative )
* Beta release on BukkitDev.
* Adaptions and fixes to combined.yawrate and combined.improbable.
* Add "strict" flag to the configuration of blockbreak.fastbreak. Similar to inventory.instantbow, setting this to false will lead to taking the time between two block break actions, not from interaction to breaking.
* The chat.logins data gets erased with reloading the configuration.
* Updated some permissions in the plugin.yml.
* Some internals, like using a logging utility where appropriate.

----

### 3.8.7-beta-b294 (cumulative)
* Beta release on BukkitDev.

### 3.8.7-b293 (cumulative)
* 1.4.6 support.
* Fix for yawrate.
* Fix walking on brewing stands.
* Better precise lag spike counting.

----

### 3.8.6-beta-b285 (cumulative)
* Beta release on BukkitDev.

### 3.8.6-b284 (cumulative)
* Compatibility series (beta) for 1.4 (CB2511 -> CB 2512).
* Might work with all builds 1.4.2 ... 1.4.5.
* Various bug fixes since the x1 build (survivalfly, bed-leave, lag, other).
* Disable managelisteners option, needs to manually reset the flag, or regenerate the entry/config.
* Spawn-egg dupe-prevention is bound to the inventory.items check being active, to allow turning it off.
* Munchhausen check added, could be activated if you have trouble with players using a fishing rod for flying. (Now official tribute to BergerKiller, deactivated by default.)

----

### --Bridge-MC_1_4-y2-DEV--### 
* <<color red>>This build contains bugs! It's not recommended to use it anymore.<</color>>
* Compatibility release (beta) for 1.4 (CB2511 -> CB 2512).
* Might work with all builds 1.4.2 ... 1.4.5.
* <<color RED>>This build can not be found on our Jenkins site.<</color>>

----

### --Bridge-CB2411_CB2412-x1--### 
* <<color red>>This build contains bugs! It's not recommended to use it anymore.<</color>>
* Compatibility release (beta) for 1.4 (CB2511 -> CB 2512).
* Might work with all builds 1.4.2 ... 1.4.5.
* <<color RED>>This build can not be found on our Jenkins site.<</color>>

### 3.8.5-b274 (cumulative)
* Fix aspects of NoFall.
* Add command to display lag.

----

### 3.8.4-RC-b271### 
* Release on BukkitDev.

### 3.8.4-b270 (cumulative)
* More sharp no-fall check.
* Remove undoing command changes on disabling (caused issues with permissions).
* Using a block-cache for ground checks with block breaking too.

----

### 3.8.3-RC-b267### 
* Release on BukkitDev. //Accidentally deleted.//

### 3.8.3-b266 (**Release phase**, cumulative)
* To be verified (bleeding):
    * Fix survivalfly violations for being stuck in sand and similar.
    * Attempt to improve performance with collecting some blocks properties beforehand to be able to check for quick returns.
* Alterations to cleanup on disabling the plugin.
* Changed synchronization of TickTask.
* Added debug messages during disabling of the plugin (logging.debug).

### 3.8.3-b261 (cumulative)
* CraftBukkit dependency: 1.4.5 (..., should be backwards compatible to 1.4.2).
* Split off a bed-leave  check.
* Switch blockplace.fastplace to shortterm + 2 secs.
* More kick actions for higher vls (delayed for moving!).
* Revised and corrected parts of moving set-backs and the passable check.
* **Fix crash exploit.**

### 3.8.3-b253 (cumulative)
* CraftBukkit dependency: 1.4.4-R0.1
* Adapt to 1.4.4.
* Compatibility with 1.4.2.
* Fix for custom snow heights.
* Add safeguards for MC API access.
* Spawn-egg dupe prevention.

----

### 3.8.1-RC-b244### 
* Release on BukkitDev.

### 3.8.1-b243 (cumulative)
* Instantbow has a "strict" flag now. For laggy servers should be better set to false.
* Fight.angle: now yawrate checking for fight is bound to this, so it can be disabled with fight.angle.
* Sharpened survivalfly and nofall.
* Changed "protectplugins" to alter permission defaults.
* Added tab completion for ncp-commands, for convenience.
* Bugfixes
    * Fastbreak.
    * More blocks to be walked on (flower pot, cocoa beans, ...).
    * Adjustments to the set-back logic for moving checks.
    * Vertical accounting for survivalfly.
    * Various others.
* A range of performance optimizations.
    * Check some permissions for moving checks only if the player is moving faster than expected.
    * Use internal caching for most moving checks, get rid of bounding box creation mostly.
    * Create optimized action lists for internal use (not containing actions that never get executed anyway).
    * Caching results from checking block ids and data.
    * Create slightly less history entries.
* API extended. Managed listeners option for future compatibility improvements (not sure it wins any performance though).

----

### 3.8.0-RC-b207 (**Release**)
* Release for 1.4(.2) on BukkitDev.

### 3.8.0-b206 (**Release phase**, cumulative)
* Dependency set to CraftBukkit 1.4.2-R0.1 to match the beta release of CraftBukkit.
* Use slightly bigger bounding box for stairs. (Attempts to reduce false positives).
* Adapt instanbow default settings (**configuration change**).

### 3.8.0-b204 (cumulative)
* Developement for 1.4(.2) CraftBukkit snapshots.
* Fix jump boost.
* Avoid resetting set back in case of a workaround (few to none effect).

----

### 3.7.10-RC-MC1.3.2-b201### 
* **1.3.2 BACKPORT RELEASE (InventoryClick).**
* Hotfix inventory click.

### 3.7.10-b200 (cumulative)
* Adaption to CraftBukkit development builds for 1.4(.2).
\\(Mainly new block types with their breaking and bounding box properties.)
* FastClick: Added Option to spare players in creative mode from the fastclick check.
* Several adaptions to attempt to reduce false positives in survivalfly.

----

### 3.7.9-RC-b191 (Release)
* Release on BukkitDev (**critical hotfix for enchanted books**).

### 3.7.9-b190 (cumulative)
* Critical hotfix for enchanted books.
* Instanteat and Instantbow: Make these actually work, instantbow does have false positives still.

----

### 3.7.8-RC-b182 (Release)
* Release on BukkitDev (finally).

----

### 3.7.7-RC-b178 (Release)
* --Release on BukkitDev.--

----

### 3.7.7-RC-MC1.3.1-b177 (Release)
* Last "backport" release for MC1.3.1 on jenkins only.

### 3.7.7-b176 (Release phase, cumulative)
* NoFall: Set fall distance on logout, remove actions from default config.
* Fixes for godmode: check permission + active, remove use of old obfuscated method, changed since. [Parts of this check might get removed: obsolete.]

### 3.7.6-b174### 
* --Release on BukkitDev.-- //(cancelled due to long present problem with godmode demanding adaptions)//\\No reason to become nervous :) - just approval takes > 5-10 hours, so i will re-upload.

### 3.7.6-b173 (Release phase, cumulative)
* FastBreak: Reduce vl by factor 1000.
* FastBreak: Workarounds for wood and stone tools.
* **Configuration changes!**

### 3.7.5-RC-b171
* --Release on BukkitDev.-- //(cancelled due to bugs found + approval not done until then)//
* Users of CompatNoCheatPlus should update to the latest release of cncp.

----

### 3.7.5-RC-1.3.1-b170### 
* "Backport" release for 1.3.1 (only on jenkins).
* Users of CompaNoCheatPlus should update to the backport release of cncp.

### 3.7.5-b169 (**Release phase**, cumulative)
* Fix for survivalfly (repeaters).
* Fix NPE (teleport).
* Passable: Ignore ladders be default.
* API adjustments and additions to make some things accessible.
* Adjustments to position resetting for moving checks.

### 3.7.5-b164 (**Release phase**, cumulative)
* Set dependency to CraftBukkit 1.3.2-R2.0
* chat.text: some of the weights will now be weighted by time passed as well to make it slightly less aggressive (mainly message repetition).
* survivalfly: Prevent VL reduction if violations are less tan 2 seconds ago (aims at certain bypass attempts to make them violate higher vls).
* nofall: consistently reset nofall data on fall damage events.
* Fixes for survivalfly (stairs).
* Fixes for yawrate (maximum penalty, use the yaw that the player is moving towards).
* Fixes for passable (allow moving if head is free).
* Slight API extension (changes if not using AbstractNCPHook). **cncp needs updating!**
* Completely remove nomovedtooquickly remainders (NetServerHandler).
* Configuration changes !

----

### 3.7.4-RC-b156 (**Release**)
* Release on BukkitDev

### 3.7.4-b155 (Release phase, cumulative)
* Passable + cactus.
* Ladder + efficiency-axes.
* Only alert for outdated config if needed.
* Reduce false positives i survivalfly.
* Account for fences with the on-ground judgements.

### 3.7.4-b153 (cumulative)
* Passable check has more safeguards against moving inside of blocks.
* On-ground checking has an anti-spider feature now (ignore blocks that have colliding solid blocks above).
* Performance improvements for moving checks, but also features added (accounting, anti spider).
* Fixes.

### 3.7.4-b145### 
* Adjust survivalfly, fighting checks...
* Delete all data and history if the system time ran backwards.
* No more teleporting of players: instead remove the invulnerability after login and check the damage events to decide if to apply certain kinds of damage.
* Fixes and optimizations. Config changes...

### 3.7.4-b127### 
* **Big change:** Chat section re-organized, merged nopwnage+globalchat into "text". Added checks to treat commands, relog and global logins individually.

### 3.7.4-b124 (cumulative)
* Various minor fixes.
* Begin to re-structure chat section,

----

### 3.7.3-b111 (**beta release on bukkitdev**,cumulative)
* (111) Fix wrong speed check vl being added to history.
* Cleanup flying permissions: creativefly bypass now also bypasses survivalfly by default. Slight optimization.
* Fixes to fastbreak (enderchest), adapt logging output for fastbreak to show used and expected times for each block as well.
* Adapt checks to be more effective against forcefields, include a distance-penalty for hitting at long distances and a time-penalty for turning too much.
* Make configurable if to ignor creative mode or the allowFlight setting for using the creativefly check.
* Add data expiration management to enable you to release some memory.
* Add savebackconfig setting to allow minimal per-world configs.
* Various adjustments and optimizations.

### 3.7.2-beta-b96 (**beta release on bukkitdev**)
* Minor adjustments, world config fixed for a part.

### 3.7.1-beta-b95 (**beta release on bukkitdev**, cumulative)
* Setting version to 3.7.1... to not risk mix ups with the earliest builds (it happens!).
* Small adjustments and fixes.
* Cleanup command usage output a bit, add commands for exemption.
* Remove checkforupdates for the moment.

\\//From here on only bug fixes and configuraton changes will make it into the beta release.//

### 3.7.0-b92### 
* Internal API changes: cncp must be updated**!
* Disable captcha by default. instead deny to login for some time. Rearm nopwnage slightly (vl is kept now and decreases with normal messages).
* Adjust configuration in some places.
* Change config path: chat.globalchat.commands -> chat.handleaschat
* Add kicklist and unkick commands.

### 3.7.0-b91 (cumulative)
* Only add defaults to world configs, that belong there, warn if entries are present that only should or only can be set in the global configuration file.
* Fix world configs not being recognized.

### 3.7.0-b88 (cumulative)
* Mostly fixes for fastbreak (important).
* Add level to wrong block check, and let it trigger much less often.
* Improvements for commands (remove removes also history, works for data of players that went offline).

### --3.7.0-b86-- (cumulative, feature complete)
* (b86) Important fixes for fastbreak.
* Reorganize fast breaking: fastbreak will be the new check, blockbreak.frequency will be the check limiting the breaking frequency even for insta breaking.
* Allow creative to insta break.
* Allow insta break leaves with efficiency>1, adjust durationfor leaves for efficiency 1.
* Contains a more exact fast break check, taking into account individual blocks and enchantments. Needs further testing.
* Improvement for wrong-blobk check.
* Might need more balancing, reports about blocks/tools/enhantments combinations conflicting with fastbreak most welcome (//only if oldcheck is set to false...//)!

### 3.7.0-b82 (**beta candidate**)
* Violation level of wrong-block check decreases with time now.
* Added internals for better fast break checks (few difference).

### --3.7.0-b81--
* Simplify and optimize violation handling and actions execution (small bug probability).
* Adjust KnockBack check to only count start of sprinting, not end of sprinting.

### --3.7.0-b80-- (cumulative)
* Add command "ncp removeplayer", to remove player violation data. The globalchat engine datas (holding typed words etc.) will not be reset by this, but that expires after about 30 seconds anyway.
* Add "wrong block" check (block break).
* Add "improbable" check (combined: several indications of improbable behavior, like speeds, hitting on max distance, other violations).
* Add "ncp tempkick (player) (minutes)..."\\//(Denies login, does not save kicked players.)//

### --3.7.0-b78-- 
* Fix check type not displaying correctly on ncp info.

### --3.7.0-b77-- (cumulative)
    *Consider --Builds 73 to 76 broken!-- use 77 up.**
* Critical fix over --73 to 76--: Actions endless repetition.
* Important fix: blockbreak / fastbreak.
* Fix: range for globalchat/similarity is now read from the config.
* Chat updates players permission states on world changes.
* Rework asynchronous actions execution handling - demands of hooks for chat to allow processing in another thread than the main thread.
* Tweak nofall (less extra on-ground checking).
* Make tolerance for step check configurable, defaulting to 0.1: checks.moving.survivalfly.ystep  -  maximally close to below 0.5, players moving up for 1 +- tolerance get reset (in short).

### --3.7.0-b72--
* Update permissions in plugin.yml

### --3.7.0-b71-- (cumulative)
* Add: selfhit check.
* Fix: Global config does not overwrite on reading errors.
* nomovedtooquickly settings are hidden now (too much confusion with versions / 1.3.1 servers with 1.3.2 clients etc.)
* globalchat: add hidden active flags for global and player sections (work in per world configs).
* Remove ban/ip actions from nopwnage checks default actions.
* All kick commands done from chat checks should use delayed kicks (dafaults adjusted: ncp delay ...).

### --3.7.0-b68--
* globalchat
    * Renaming of the engine config section. global/player: words, prefixes.\\**Removes the engine section, and engine.active setting**\\The extended checks have to be activated individually , global and per player method sections can have a weight to be multiplied with the results, further settings available. By default all are turned off.
    * nopwnage.debug/globlachat.debug: true outputs scoring info to the console.
    * globalchat.maximum: false Will sum up engine scores instead of using the maximum.
    * Adding a similarity check.
* Fixes. Nopwnage vl accumulates now correctly.
* captcha: Removed some letters from the defaults.

### --3.7.0-b67--
* Important fix for glcompressedwords (only relevant if enabled).
* Potential fixes for startup issues.

### --3.7.0-b66--
* nopwnage.speed.weight: 100
* globalchat.level: 80
* globalchat.engine.active: false
* globalchat.engine.glcompressedwords.active: false
\\//Reloading resets chat violation data, now.//

