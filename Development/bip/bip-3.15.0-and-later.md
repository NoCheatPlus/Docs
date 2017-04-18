## Build Infos Page - NoCheatPlus 3.15.0 and later.

[Back to the Build-Infos overview.](https://github.com/NoCheatPlus/Docs/wiki/Build-Infos)

----

### 3.15.2-SNAPSHOT-sMD5NET-b1086(cumulative)
* Release type: [BLEEDING]
* Configuration
    * For inventory.instantbow you can control how it uses the improbable check (feed/weight/turn off with 0.0 weight).
* Fixes
    * Potential fix: Model the '(noob) tower up' with lost-ground checks instead of the odd/optimistic set-back-y adjustment.
    * Fix for a friction envelope check (uncertain impact, might render a workaround functional, or allow flying :p... perhaps not).

### 3.15.1-RC-sMD5NET-b1084
* Release type: **RC Release**
* Supported versions of Minecraft (CraftBukkit/Spigot)
    * Focus: 1.11.2
    * Supported: 1.4.5-R1.0 - 1.11.2
* Download at Jenkins: https://ci.md-5.net/job/NoCheatPlus/1084/
* Hashes
    * MD5: b795f989bd8d4eb0e4e4e3bffeca5c01
    * SHA512: 94d3d548d4eaeac6aa3ee2deda958de931d62fcb7510450145c4c6eedc9aacc67df905dd822aa634595b72a61215a548a7cb6b6d25dcf3d7c02c44b629564dc5
    * File size: 1358310

### 3.15.0-SNAPSHOT-sMD5NET-b1083(cumulative)
* Release type: development
* Topic: Internal data storage overhaul (ongoing) of uncertain impact. Fixes.
* New
    * Data removal can be done for sub checks (So far: FIGHT, COMBINED, MOVING).
    * COMBINED_YAWRATE allows exemption and precise data removal.
* Fixes
    * Fix creativefly and survivalfly actions.
    * Fix configuration notifications.
    * Distinguish set-back options by Minecraft version by default.
    * Fix handling of PlayerMoveEvent cancelled by other plugins.
    * BlockInteract: null blocks.
* Internals
    * Work towards a more unified player specific data storage.
    * PlayerData holds access for player specific on-tick tasks.
    * (Allow overriding the set-back method via hidden settings.)

### 3.15.0-SNAPSHOT-sMD5NET-b1075(cumulative)
* Release type: _deficient_
* Topic: New set-back method, recommended for 1.11.2 and later (post-2017-03-24).
* BUGS:
    * Actions for survivalfly and creativefly: spaces missing with 'cancelvl' which should be 'cancel vl'.
    * Flying exploits: For MC before 1.9 set _checks.moving.setback.method_ to "set_to", to force legacy behavior - only b1075 and before. For builds from 1078 on, the configuration value can be removed.
    * PlayerMoveEvent cancelled by other plugins: Fixed in build 1079.
* Fixes
    * Ignore arrow types for vehicle checks (can be overridden with hidden settings).
    * Set back handling (moving checks): hybrid approach (schedule + attempt immediate), to avoid TeleportCause.PLUGIN for setting back players. Avoid unnecessary teleporting.
    * Attempt to fix (selected) issues concerning vehicles with multiple passengers.
    * Fix or work around an exquisite selection of random issues.
* Internals
    * Skip sweep attack detection, when the DamageCause is present.
    * Use Bukkit methods once available (Entity.getHeight|getWidth).

### 3.15.0-SNAPSHOT-sMD5NET-b1066(cumulative)
* Release type: development, sitting duck.
    * INFO: Use to avoid bleeding edge for pre-1.11.2 (pre-2017-03-24).
* New
    * Block change tracking.
        * Opportunistic passable checking, accounting for past block changes (pistons, redstone driven blocks: door-like, not for interaction nor directly next to button/lever).
        * Standing/moving on blocks that have just been changed.
        * Slime blocks + pistons (ongoing).
        * Horizontal push by pistons.
    * Elytra boost support.
    * More effective horizontal speed limiting (hacc).
    * New block flag to make water_lily compatible with 1.8.8 clients (water_lily: ground+ign_passable+ground_height+height8_1). This is not set by default.
    * Support plugins injecting and removing fake block changes (global only).
* Configuration
    * Per-configuration entry warnings, in case a new default value is set.
* Fixes
    * Prevent letting Minecraft deal fall damage for micro moves (self damage, speeding).
    * Elytra in creative mode, when not flying.
    * 1.11 blocks, native access module.
    * Detect horses correctly on 1.11.
    * Allow ProtocolLib 4.2.0 for MC 1.11.
    * Go easier on long messages (chat.text / 1.11).
    * Extend the CB-Reflect module to access entity height/width/box, fix block shape access on 1.11.
    * Internal registry fixes.
    * FastConsume: also disable instanteat after reloading the configuration.
    * Fix Double.MAX_VALUE violations with fight.direction.
    * Passable: 2-high ceiling on 1.10.2.
    * Passable: Ignore sneaking for bounding box height.
    * SurvivalFly: allow vertical friction on ladder without velocity being present.
    * Adjusted configuration of supported ProtocolLib versions.
    * Attempt to work around a bug where the player position is not updated on teleporting to the end (on some server/s versions).
    * Fixes for the on-ground logic (variable/fences, potential abuse).
    * Vehicle enter: fix nested vehicle check.
    * Improve compatibility (net: UnsupportedOperationException).
    * Don't use short cuts for dealing with NaN and infinity.
    * Register .silent check permissions. Add nocheatplus.checks.inventory.open to plugin.yml.
    * NullPointerException with BlockProperties.isSameShape.
* Internals
    * Minor optimization (NET: if none are enabled).
    * Work towards block change compatibility further.
    * Use stored world names for packet frequency if world is null.

### 3.15.0-SNAPSHOT-sMD5NET-b1022(mostly stable, cumulative)
* Release type: **mostly stable**
* Supported versions of Minecraft (CraftBukkit/Spigot)
    * Focus: 1.10.2
    * Supported: 1.4.5-R1.0 - 1.10.2
* Download at Jenkins: https://ci.md-5.net/job/NoCheatPlus/1022/
* Hashes
    * MD5: 8da1ffcf13158496d6eca0c9d04cc51e
    * SHA512: 59e794efb529399cf8433c8cacf58bf25a7fac05421e4ff9fad72f6a4dee92a3f75e6603b5ff2b899ee5bc131580491d021da3fc95fdc81213beddef80163870
    * File size: 1271668
* New
    * MC 1.10 support.
    * Basic vehicle fly checks for more than boats.
    * Ability and configuration for loading chunks for moving, teleport and world change.
    * Hot fix for 1.9/1.10 falling block duplication with end portals.
    * The moving.passable check now accounts for the full bounds of a player.
    * Overall packet frequency check for pre-1.9 (ProtocolLib).
* Configuration
    * Remove compatibility.blocks.ignorepassable (use overrideflags instead).
    * Add default entry for piston_moving_piece (overrideflags).
    * Kick messages for illegal player and vehicle moves are configurable.
* Fixes
    * Passable: Fix moving on soil (1.10.x).
    * SurvivalFly: Fix climbing up trap door above ladder.
    * Fix block flags for for fence-like blocks.
    * Fix low food level sprinting with players who are allowed to toggle flight.
    * Vehicles: falling with minecarts.
    * Confine climbing speed more.
    * Fix off-hand issue with blockplace.
    * Reactivate net.sounddistance for 1.9 and later.
    * Update the CB-Reflect module for past 1.9.
    * Attempt to fix issues with fake players with fight checks.
    * (Attempt to improve ladder/vine + velocity.)
    * Allow higher ProtocolLib versions on MC 1.10.
* Other changes
    * Remove compatibility module for Glowstone (legacy).
* Internals
    * [BREAKING] Change build profiles: ncp_base must be active always.
    * [BREAKING] Moving classes/interfaces around.
    * [BREAKING] MCAccess: split off more fine grained providers.
    * Extend debug logging for blockinteract (rate-limited).
    * Add build profile for 1.7_r4 (MC 1.7.10).

