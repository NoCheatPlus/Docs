Build Infos Page - NoCheatPlus 3.13.7 and later.

**These builds are outdated.**

[Back to the Build-Infos overview.](https://github.com/NoCheatPlus/Docs/wiki/Build-Infos)

----

### 3.14.0-SNAPSHOT-sMD5NET-b989(mostly stable, cumulative)
* Release type: **mostly stable**
* Supported versions of Minecraft (CraftBukkit/Spigot)
    * Focus: 1.9.4
    * Supported: 1.4.5-R1.0 - 1.9.4
* Download at Jenkins: https://ci.md-5.net/job/NoCheatPlus/989/
* Hashes
    * MD5: f14bcc06f982d4d75750e36897716820
    * SHA512: 73565272d83ca943118cbd8cea9891dc02fab1a539c26f8cb909ea7b3fefc5e92ea0e2f07901a2209e2f64f47ca6d96da986f4b4c1a9f6aa919eb76ad60c6ce9
    * File size: 1165971
* New
    * MC 1.9.4 compatibility.
    * Basic boat fly check.
    * Exempt NPCs from all checks by default.
    * 'ncp stopwatch' for testing.
* Configuration
    * Create a new vehicle section, change related paths.
    * The temporary login denial message is now configurable (strings.msgtempdenylogin).
    * Configure exemption by meta data and exemption for NPCs.
    * Add configuration for boatsanywhere (place on land).
    * Change default for 'ignoreallowflight' to true.
* Fixes
    * Sweep attack detection (AoE).
    * StackOverflowError with inventory.open and a blacklist kick by WorldGuard.
    * NoFall: Skip dealing damage to players who are allowed to fly.
    * SurvivalFly: Fix climbing up trap door above ladder. (partial)
    * Prevent another variant of packet-based speeding.
    * Vehicles: Fix vehicle detection for missing vehicle events.
    * Vehicles: set-back handling.
    * Support higher levels of the levitation effect.
    * Improve vertical piston support (not finished, not yet officially activated).
    * TO BE TESTED: Allow vertical velocity on ladders and vines (once).
    * Account for off hand in (hopefully) all relevant places.
    * Also recognize ProtocolLib versions just with build number prefix.
    * Do not check for meta data off the primary thread.
* Internals
    * Debug only: unused vertical velocity tracking.
    * [BREAKING] Larger refactoring and changes for vehicle fly checks (mostly unify/change location and set-back handling).
    * Hard teleport on vehicle set-backs by default, from within other event handling.
    * Location trace doesn't merge entries anymore (fight / latency).
    * Extend/alter debug logging.
    * Added GPLv3 headers to source files.

### 3.14.0-SNAPSHOT-sMD5NET-b960(mostly stable, cumulative)
* MC 1.9
    * Blocks break data and flags.
    * Dedicated MCAccess module for CB with MC 1.9.
    * Allow standing on shulkers.
    * Rough levitation support.
    * Very coarse elytra support, hardly safe vs. abuse. _Note recent configuration overrides (not advertised!)._
    * Allow versions of ProtocolLib with MC 1.9 (currently disable SoundDistance): 3.7, 3.7.0, 4.0.0 or later.
    * Ignore sweep attack follow up damage.
    * "Noob tower": jumping upwards, building underneath.
    * Ignore multi-block place of bedrock and ender crystals.
    * Block place: check the placed material instead of what's in main hand, if available.
    * Disable FastHeal with MC 1.9.
    * (Still enable the pvp-knockback workaround with MC 1.9.)
* Configuration
    * Change creativefly model configurations (default speeds for elytra and spectator).
    * Increase hover login ticks to 60 (previously 0).
* Fixes
    * More cases with splashing through water.
    * creativefly
     * Fix violation skipping/cooldown mechanics. This might increase violation levels.
     * Fix set back handling (maxheight).
     * Fly-nofly transition: Reduce [ERROR].
    * Player instances stored wrongly.
* Internals
    * Add more minimized build profiles to pinpoint Spigot 1.8.8/1.9.
    * Organize some workaround code better.
    * Extend/alter debug logging.

### 3.13.8-SNAPSHOT-sMD5NET-b930(cumulative)
* New
    * A quick check for extreme moves.
* Fixes
    * Portal events: only clear data if a location is present, add debug log.
    * FastClick: Don't add violation twice for display.
    * Fix HashMapLow (bucket position).
* Changes
    * Handle system time running backwards differently.
    * Adjust log message for ProtocolLib.
* Internals
    * [BREAKING] Add a penalty framework. Breaks internal API, see commit messages and diffs.
    * Catch unintended input somewhere.

###3.13.7-RC-sMD5NET-b925###
* Recommended Release (milestone release).
    * MD5: d27d11a413b1ef0f6875959f9af806e7
    * SHA512: 9382f7d2dc8edc05104a5f56998c42803678de45ea32768015609e638d1d783febd56d7912766dabe0ae802c2fbd3cc152f686876599f8af6bd12276c54e46d9
    * File size: 1032874
* Internals
    * Use internal registry for a Random instance.

