In order to test out bugs better you have three major options.

**All these options are not really meant for (big) production servers, they can cause extreme console output and performance issues.**

Mostly console output will be interesting, but also the in-game chat might be useful, check the output-client.log file to not need to use screenshots.

If you try to report a false positive and want to help finding the causes faster this can be very helpful. Rather send a little longer log not to miss out parts, so unless familiar with it you should add a little before and after the violation message of TestNCP for instance. For moving always at least from jumpphase=0 until the violation and "set back to..." a couple of lines below. If possible or not sure it is a singular issue, include a couple of violations.

**Please use a paste or send as a file attachment by mail if the output is a little bit longer.**

# NCP Debug Output

For the most detailed output use a development build of NCP (or manually edit BuildParameters.properties in the jar and set DEBUG_LEVEL to something like 10000).

Then set a/the check-group debug flag, like //moving.debug// to true.

NoCheatPlus allows to set debug flags for almost all check groups. The flag in the logging section can also be set, but it will not lead to more check-output.


# TestNCP
This plugin is found at the project site of [NCPTools]. 
TestNCP allows you receiving console and in-game output for every violation, even if logging would not normally show the message due to low VL for instance.

The plugins configuration allows setting testers, wither '*' for all players (spam), or the player names for distinct players.

Input about violations can be confined to individual players using _/testncp input (player)_

# EventMirror
This plugin is found at the project site of [NCPTools]. 
EventMirror sends in-game info about players actions, to allow checking if certain events happened at all. It does not cover all existing events, though.

Any Player can use _/mirror_ to receive events in-game. The messages are restricted to the player that is involved.

Use _nocheatplus.admin.debug_ permission to get more debug informations.

[NCPTools]: http://dev.bukkit.org/bukkit-mods/ncptools/
