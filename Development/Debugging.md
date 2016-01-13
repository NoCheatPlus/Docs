# Create Debug Output

**Most of these options are not really meant to be used on (big) live/production servers, they can cause extreme amounts of log file output and result in performance issues.**

NoCheatPlus allows you to generate debug logs in various ways. With this you can help us tracking issues or cheats, by generating debug output selectively and providing us a paste link, or link/send a compressed file. 

Mostly console output will be interesting, but also the in-game chat might be useful, check the output-client.log file to not need to use screenshots, unless for showing map/block setups.

If you try to report a false positive and want to help finding the causes faster this can be very helpful. Rather send a little longer log not to miss out parts, so unless familiar with it you should add a little before and after the violation message of TestNCP for instance. For moving always at least from jumpphase=0 until the violation and "set back to..." a couple of lines below. If possible or not sure it is a singular issue, include a couple of violations.

**Please use a paste or send as a (compressed) file attachment by mail if the output is a little bit longer.**

If sending a server log, you might want to ensure to not expose any sensitive data, such as logged session keys, ips or whatever your log may contain.

### Debug flags in the configuration
You can manually enable permanent debugging with setting a/the check-group debug flag, like _checks.moving.debug_ to true. Debugging all checks can be done with setting _checks.debug_ to true. Additional output can be generated with enabling logging.extended.status.

NoCheatPlus allows to set debug flags for almost all check groups. The flag in the logging section can also be set, but it will not lead to more check-related output. Some debugging output is only generated, if the configuration flags are set, e.g. with ProtocolLib.

This is not meant for production servers with many players on, due to the amount of logging done with each move for each player. For production servers we recommend using on-the-fly debugging rather.

### On-the-fly debug output for individual players
Using the command _/ncp debug player (player)_ allows you to start debug logging for a player. The output is written to the log file specified in the configuration (not to the console).

The debug logging may reset with the player logging out. In order to turn on-the-fly debugging off, you can either use _/ncp remove (player)_ or _/ncp reload_ , with the latter removing all data for all players.

For more confined output you can set the log file to a folder name, such as "logs". Then you can use _/ncp reload_ before and after debugging players, and the output will be confined to one log file. DrawBack is that this call is slightly heavier, due to affecting all players data and also due to reloading the configuration.

With using _/ncp reload_ repeatedly, e.g. for recording individual sequences to individual files, you'd have to repeat _/ncp debug player (player)_, because on-the-fly debugging will reset with reloading the configuration.

### Debug level (Legacy)
For the most detailed output use a development build of NCP (or manually edit BuildParameters.properties in the jar and set DEBUG_LEVEL to something like 10000).

### Allviolations hook
NCP can log all violations of all players to the console and/or to the ingame notification channel. You can activate the allviolations hook in the configuration, under logging.extended.allviolations. If you want more fine grained control over who sees those notifications and whose output you want to see, use TestNCP from the NCPTools collection (see below).

# NCPTools

NCPTools at BukkitDev (http://dev.bukkit.org/bukkit-mods/ncptools/) is a collection of tools we use for testing and debugging with NoCheatPlus.

These tools are meant for testing and debugging with test servers.

See the README.txt in the zip file or on the download page for more details.

### FightHelper
Reduce all damage to 1 or 0, so the player does not die, keep restoring health. Meant for continuous combat testing, without need for respawning and teleporting all the time. This might affect some plugins or calculations due to the reduced damage - e.g. god mode will behave differently with this on. 

### MoreCommands
Add more commands under /morecommands (/more), that are useful for setting up a test server. One permission per command (morecommands.command[.subcommandname]). Most commands are not meant for ordinary staff.
Setting up a test server (or admin-only, DESTRUCTIVE!):
* more op : Set op and creative mode at once.
* more ordinary : Remove op and set to survival mode.
* more pyramid : Create pyramids with a bedrock base and other blocks on top (snow layers, stairs, steps, water/lava, any blocks).
* more setradius : Set blocks within xz-radius (and between up to two y-offsets, from the block you stand on).
* more snowlayer : Place random height snowlayer on top of existing blocks within some radius.
* more setspawn : Set world spawn.
Testing:
* more food : Stack up food or add bread.
* more heal : Heal + hunger.
* more seteffect EFFECT@mc-levelxseconds : Set potion effects hard (no args is remove all).
* more spawn : Teleport to the world spawn.
* more velocity : Add velocity.
* more fly : toggle flying.
* more walkspeed
* more flyspeed
* more permissions : list effective permissions of a player, allowing to confine output to sub-nodes of given arguments.
* more day : Set day time and fine weather.

### MoveLogger
Log all moves by all player to the console. Meant to track issues with logging or if NCP is not there, to be able to compare.

### SimpleConfigEditor
Handle with care: Simplistic ingame configuration editing, no safety whatsoever, not for ordinary staff - avoid typos :), especially with tab completion (e.g. save config to WorldGuard.jar).
File: sce.ja
Command: /simpleconfigeditor or /sce (simpleconfigeditor.command)
Sub commands:
- 

### TestNCP
This plugin is found at the project site of [NCPTools]. 
TestNCP allows you receiving console and in-game output for every violation, even if logging would not normally show the message due to low VL for instance.

The plugins configuration allows setting testers, wither '*' for all players (spam), or the player names for distinct players.

Input about violations can be confined to individual players using _/testncp input (player)_

### EventMirror (Legacy, not contained in the collection at present)
This plugin is found at the project site of [NCPTools]. 
EventMirror sends in-game info about players actions, to allow checking if certain events happened at all. It does not cover all existing events, though.

Any Player can use _/mirror_ to receive events in-game. The messages are restricted to the player that is involved.

Use _nocheatplus.admin.debug_ permission to get more debug informations.

