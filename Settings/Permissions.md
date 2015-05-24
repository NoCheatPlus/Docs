**Table of context**
* [Shortcuts](Permissions#shortcuts)
* [Checks](Permissions#checks)
 * [Blockbreak](Permissions#blockbreak)
 * [Bypass](Permissions#bypass)
* [Commands](Permissions#commands)
 * [Auxiliary commands](Permissions#auxiliary-commands)
* [Client modifications](Permissions#client-modifications)
* [Miscellaneous and parent permissions](Permissions#miscellaneous-and-parent-permissions)

# Shortcuts
`nocheatplus.shortcut.info` Gives permissions to  
`nocheatplus.shortcut.monitor` Gives permissions for  
`nocheatplus.shortcut.safeadmin` Gives permissions to  
`nocheatplus.shortcut.bypass` Gives permissions to bypass all checks.  

# Checks
`nocheatplus.checks` Will be exempted from all checks  
`nocheatplus.checks.<Check category here>` Exempts from all checks of a given check category  
`nocheatplus.checks.<Check category here>.<Check name here>` Exempts group of this check. Example: nocheatplus.checks.moving.creativefly will exempt from creativefly.

## Blockbreak
`nocheatplus.checks.blockbreak.break.liquid` Is allowed to break water/lava 

## Bypass
`nocheatplus.bypass.denylogin` Exempts from login denial

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

`nocheat.admin` Gives access to all [NoCheatPlus commands](https://github.com/MyPictures/NoCheatPlus/wiki/Commands) including Auxiliary ones  
`nocheatplus.notify` Will receive hack notifications over in-game chat

**Notes**
* By default NoCheatPlus assigns all permissions and gives full rights to players that have been `/op-ed` on your server. If you don't want to give OPs full access to all NoCheatPlus features then take a look in the configuration of your permissions plugin (Example with PermissionsEx: allowOps: false).

**Related**
* [Client Modifications](Client-Modifications)
* [Checks](Checks)
* [Commands](Commands)

[CJB Mods]:http://cjbmods.com/
[Rei's Minimap]:http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-mods/1275219-jul-08-reis-minimap-v3-4_01
[Smart Moving]:http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-mods/1274224-smart-moving
[Zombe's modpack]:http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-mods/mod-packs/1272345-zombes-modpack-26-mods-v8-2-2-upd-11-jul
[JourneyMap]:http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-mods/1278348-journeymap-5-0-1-realtime-mapping-in-game-or-in-a