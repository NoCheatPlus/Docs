**Table of context**
* [Shortcuts](Permissions#shortcuts)
* [Checks](Permissions#checks)
 * [Specific](Permissions#specific)
* [Commands](Permissions#commands)
 * [Auxiliary commands](Permissions#auxiliary-commands)
* [Client modifications](Permissions#client-modifications)
* [Miscellaneous and parent permissions](Permissions#miscellaneous-and-parent-permissions)
* [Configure permission checking behavior](Permissions#Configure permission checking behavior)

# Shortcuts
`nocheatplus.shortcut.info` Gives permissions to  
`nocheatplus.shortcut.monitor` Gives permissions for  
`nocheatplus.shortcut.safeadmin` Gives permissions to  
`nocheatplus.shortcut.bypass` Gives permissions to bypass all checks.  

# Checks
`nocheatplus.checks` Exempts from all checks  
`nocheatplus.checks.<Check category here>` Exempts from all checks of a given check category  
`nocheatplus.checks.<Check category here>.<Check name here>` Exempts group of this check. Example: nocheatplus.checks.moving.creativefly will exempt from creativefly.

## Specific
`nocheatplus.bypass.denylogin` Exempts from login denial  
`nocheatplus.checks.blockplace.boatsanywhere` Allows to place boats on the ground (not just in water).  
`nocheatplus.checks.blockbreak.break.liquid` Allows to break water/lava  

# Commands
`nocheatplus.command.commands` Can view all NC+ commands with _/ncp commands_  
`nocheatplus.command.exempt` Can exempt players from checks with _/ncp exempt_  
`nocheatplus.command.exemptions` Can list all check exemptions of a player with _/ncp exemptions_  
`nocheatplus.command.info` Can view check violations of a player with _/ncp info_  
`nocheatplus.command.inspect` Can retrieve player status data with _/ncp inspect_  
`nocheatplus.command.lag` Can view server lag spikes with _/ncp lag_  
`nocheatplus.command.log` Can access internal debug data with _/ncp log_
`nocheatplus.command.notify` Can toggle on/off in-game cheat notifications (includes permission `nocheatplus.notify`) for _/ncp notify_ command)  
`nocheatplus.command.reload` Can reload NC+ to re-read configurations and permissions with _/ncp reload_  
`nocheatplus.command.removeplayer` Can remove a players violation history with _/ncp removeplayer_  
`nocheatplus.command.unexempt` Can unexempt a player from checks with _/ncp unexempt_  
`nocheatplus.command.version` Can view the version information with _/ncp version_  

## Auxiliary commands
`nocheatplus.command.allowlogin` Can remove temporary kicked players with _/ncp allowlogin_  
`nocheatplus.command.ban` Can ban players with _/ncp ban_  
`nocheatplus.command.delay` Can delay command execution with _/ncp delay_  
`nocheatplus.command.denylogin` Can temporary kick players with _/ncp denylogin_  
`nocheatplus.command.kick` Can kick players with _/ncp kick_  
`nocheatplus.command.kicklist` Can view all players that have been temp-kicked with _/ncp kicklist_  
`nocheatplus.command.tell` Can send private messages to players using _/ncp tell_  

# Client modifications
With those permissions you can decide which mods should not be disabled on login.

## [CJB Mods]
`nocheatplus.mods.cjb` Allows all CJB mod features.  
`nocheatplus.mods.cjb.fly` Allows to use the fly mod.  
`nocheatplus.mods.cjb.radar` Allows to use the radar/minimap.  
`nocheatplus.mods.cjb.xray` Allows to xray.  

## [Rei's Minimap]
`nocheatplus.mods.rei.cave` Enables cave rendering.  
`nocheatplus.mods.rei.radar` Enables all radar features.  
`nocheatplus.mods.rei.radar.animal` Enables the animal radar.  
`nocheatplus.mods.rei.radar.player` Enables the player radar.  
`nocheatplus.mods.rei.radar.mob` Enables the mob radar.  
`nocheatplus.mods.rei.radar.other` Enables radar for "other" entities.  
`nocheatplus.mods.rei.radar.slime` Enables the radar for slimes.  
`nocheatplus.mods.rei.radar.squid` Enables the squid radar.  

## [Smart Moving]
`nocheatplus.mods.smartmoving` Enables all smart movement featuers.  
`nocheatplus.mods.smartmoving.climbing` Enables climbing.  
`nocheatplus.mods.smartmoving.crawling` Enables crawling.  
`nocheatplus.mods.smartmoving.flying` Enables flying.  
`nocheatplus.mods.smartmoving.jumping` Enables jumping.  
`nocheatplus.mods.smartmoving.sliding` Enables sliding.  
`nocheatplus.mods.smartmoving.swimming` Enables special swimming.  

## [Zombe's modpack]
`nocheatplus.mods.zombe` Enables all featuers of the zombe mod.  
`nocheatplus.mods.zombe.cheat` Enables the cheating parts.  
`nocheatplus.mods.zombe.fly` Enables flying.  
`nocheatplus.mods.zombe.noclip` Enables nocliping.  

## [JourneyMap]
`nocheatplus.mods.journey` Enables all Journey map featuers.  
`nocheatplus.mods.journey.radar` Enables the radar.  
`nocheatplus.mods.journey.cave` Enables the cave redering.  

(I think one is missing here hmm...)

# Miscellaneous and parent permissions

`nocheatplus.admin` Gives access to all [NoCheatPlus commands](https://github.com/MyPictures/NoCheatPlus/wiki/Commands) including Auxiliary ones  
`nocheatplus.notify` Will receive hack notifications over in-game chat

Commands for which the permission got set by the protection features (hide plugins), might have altered default permissions or NoCheatPlus may have set a filter permission 'nocheatplus.filter.command.COMMAND_NAME', for the case the command was allowed to be run by everyone.

**Notes**
* By default NoCheatPlus assigns all permissions and gives full rights to players that have been `/op-ed` on your server. If you don't want to give OPs full access to all NoCheatPlus features then take a look in the configuration of your permissions plugin (Example with PermissionsEx: allowOps: false).

**Related**
* [Client Modifications](Client-Modifications)
* [Checks](Checks)
* [Commands](Commands)
* [Debugging](Debugging)

[CJB Mods]:http://cjbmods.com/
[Rei's Minimap]:http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-mods/1275219-jul-08-reis-minimap-v3-4_01
[Smart Moving]:http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-mods/1274224-smart-moving
[Zombe's modpack]:http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-mods/mod-packs/1272345-zombes-modpack-26-mods-v8-2-2-upd-11-jul
[JourneyMap]:http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-mods/1278348-journeymap-5-0-1-realtime-mapping-in-game-or-in-a

# Configure permission caching behavior
Since NoCheatPlus 3.16.1-SNAPSHOT (since build 1040) / 3.17.0-RC, permission caching has been introduced. This allows for configuration of how to check for permissions, in case permission checks turn out to consume too much performance, or in case you want to override the behavior for other reasons.

You can set a default policy and define further rules for mapping permissions to policies for individual permissions, based on wildcards, or based on regular expressions.

Policy definition:
* Fetching policy[, flag1 [,flag2]]
* Separate any parts by ' ' or ',' or ':'.
* Flags are preceded by the state '+' for true and '-' for false. Default flag states can be omitted, such as `+world` or `+offline`.
* Flags apply for invalidation, regardless of the fetching policy.

| Fetching policies | Meaning/usage |
| ALWAYS | Always check. |
| ONCE  | Once until invalidation. |
| INTERVAL:(seconds) | Only check every (seconds) seconds. |
| TRUE | Always assume permission to be set to true. |
| FALSE | Always assume permission to be set to false. |

| Policy flags| Meaning/usage |
| +offline | Invalidate permissions once the player is offline (default). Strictly this also invalidates with logging on. |
| -offline | No invalidation with leaving the server, unless +world is set (!). |
| +world | Invalidate with world changes and leaving the server (default).|
| -world | No world based invalidation. Behavior with leaving the server depends on the `offline` flag now. |

Rule definition:
* Matching rule separated by ' :: ' from a policy definition.

| Matching rule | Meaning/usage |
| `startswith: (...)` or `(...)*` | All permissions that start with the given letters. |
| `endswith: (...)` or `*(...)` | All permissions that end with the given letters. |
| `contains: (...)` or `*(...)*` | All permissions that start with the given letters. |
| `regex: (... regular expression pattern ...)` | All permissions matching the regular expression (standard java String.matches). |
(Constructions with *(...)*(...)* don't work, use regular expressions instead.)

## Default policy
* Configuration path: permissions.policy.default
* Value: string
* Content: policy definition
* Examples: 
    * `INTERVAL:10, -offline, -world` for checking every 10 seconds, ignoring world changing and leaving the server.
    * `ONCE` for checking once only, still invalidate with changing the world and with logging on/off.

## Rules
* Configuration path: permissions.policy.rules
* Value: String list.
* Content: matching rule separated by ' :: ' from a policy definition.
* The first matching rule is applies, testing in the order in which they're defined.
* Examples:
    * See default configuration...
    * `nocheatplus.checks.survivalfly.* :: FALSE, -offline, -world` Never check the sub permissions of survivalfly, assume set to false always.
    * `startswith:nocheatplus.checks.survivalfly. :: FALSE` Same as above.
    * `nocheatplus.checks.survivalfly* :: INTERVAL:10` Check the survivalfly permission and sub permission only every 10 seconds (invalidate with logging on/off and with world changing).
