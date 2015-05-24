**Table of contents**
* [General Issues](Known-Issues#general-issues)
 * [Hitting/Fighting](Known-Issues#hittingfighting)
 * [Moving/Passable](Known-Issues#movingpassable)
* [Compatibility Issues](Known-Issues#compatibility-issues)
 * [NPCs](Known-Issues#npcs)
 * [Skills, machines and other](Known-Issues#skills-machines-and-other)
 * [Super jumps and flying skills](Known-Issues#super-jumps-and-flying-skills)
 * [Tekkit, FeedTheBeast, Hexxit and all the other mod packs](Known-Issues#tekkit-feedthebeast-hexxit-and-all-the-other-mod-packs)
 * [Spout and CompatNoCheatPlus](Known-Issues#spout-and-compatnocheatplus)
 * [Passable check](Known-Issues#passable-check)
* [Other](Known-Issues#other)
 * [Special (cheat) Client-Mods](Known-Issues#special-cheat-client-mods)
 * [Minecraft Chat Apps](Known-Issues#minecraft-chat-apps)

## General Issues
Issues that are only related to NCP and occur in vanilla Minecraft.

### Hitting/Fighting
Currently there are some known issues in NoCheatPlus which might cause false positives (false cheat detection) on PvP (Player vs Player) and PvE (Player vs Environment). 
We recommend to use the "/ncp info <Player>" command to find out which checks/parts of NoCheatPlus are causing those false positives and make the affected fight checks less strict (over configuration file) based on that data. 
We are currently working on a proper fix for this problem so keep an eye on the development builds of NoCheatPlus.

Additional informations:
* The higher the latency (server and client) the worse is the hit detection
* Some players fake those informations on your server and try to make you lower your "Fight" security so always try to reproduce it by yourself.
* The checks "fight.reach" and "fight.direction" seem to make the most trouble.
* If you encounter problems with the fight.direction check then set "strict" to false in your configuration file.
* Turning down the "penalty" value for fight.direction and fight.reach check could help also.

### Moving/Passable
* If a certain block type poses problems, be it a bug or just client mods or server mods or plugins "optimizing" things, you can tweak it by configuration: [Compatibility Section](Dev-Pinboard#compatibility-section)
* Velocity handling might conflict with some plugins that provide skills like "super jump".
* Fly-settings of server and plugins: We recommend to set allow-flight to true rather, and let NCP handling the fly checks, otherwise there can be conflicts leading to new exploits or just trouble.
 * server.properties
 * Multi-World plugins (e.g. MultiVerse): These might have per-world settings for allow-flight, or other fly-related settings, which might override the servers allow-flight setting.
 * Other anti-hack plugins: Two fly checks would usually conflict, due to differing set-back policies, also due to differing false-positives. Disable all but one, we suggest you enable the one in NCP and disable the others.

## Compatibility issues
Issues that arise from using other client mods, server mods, plugins.

### NPCs
For problems with non-player-characters such as with Citizens, have a look at CompatNoCheatPlus and open a ticket for that, such usually is fixable.
Please note that using names of players that are on your server to get a pretty skin on your NPCs may cause some side effects with NoCheatPlus and other plugins (NC+ might setback the NPC instead of the player etc.).

### Skills, Machines and other
Some plugins provide extra skills like fast block breaking, or automatic mining and block placing etc. To keep it compatible with protection plugins they use custom events to tell other plugins that they break blocks. These will be interpreted by NCP and might lead to various violations.
CompatNoCheatPlus provides a platform for handling these, mcMMO, Citizens, MachinaCraft should work out of the box, others might need adapting some configuration entries (ask before doing so!), others might need additions to cncp. Keep to cncp for this and add a ticket there, these are usually easy to fix/provide.
### Super jumps and flying skills
These provide problems to make compatible, though it is not impossible technically. Currently mostly not compatible.

### Tekkit, FeedTheBeast, Hexxit and all the other mod packs
* Many blocks that tekkit and other use are unknown to NoCheatPlus, block breaking speeds should be assumed as instantaneous break (would allow playing , but also fast break cheating).
* The passable check might not know the shape of some blocks, at the risk of allowing noclip hacks, those can be added to the ignorepassable list in the NCP configuration.
* Weapons such as wands from Thaumcraft that use special fighting ability's will trigger some fight checks of NoCheatPlus since NCP doesn't know this kind of fighting style.
* Going trough TwilightForest portals will trigger SurvivalFly because of this mode having strange movement while the player is teleported to the other world.
* NoCheatPlus will most likely block FakePlayers because of the bukkit superperms not supporting any "offline players". To make them compatible with NoCheatPlus you need to set "FakeJoin" to true so FakePlayers send fake login events to the server (might cause other issues).
* Placing blocks without any at*tachment on the ground such as cables or similar will trigger the "AgainstAir" check of NoCheatPlus. To workaround this issue give your default users group the "nocheatplus.checks.blockplace.against.air" permission.
* Jet packs and other "fly" tools are most likely incompatible with the SurvivalFly check.

### Spout and CompatNoCheatPlus
CompatNoCheatPlus and Spout seem to have issues, however I am not sure if they were due to unlucky versions mixed (to be tested/updated). You need to disable the Player-class hook in CompatNoCheatPlus for sure! Otherwise NoCheatPlus will get unusable on your spout server.

### Passable check
The SpoutCraft client seems to allow moving into the corners of fence-arrangements, which is not possible in vanilla. Ladders can be added to the ignorepassable list in the config of NCP.

## Other
All issues that didn't fit in any category above are listed here.

### Special (cheat) Client-Mods
Some client mods do non-vanilla moving stuff that can conflict with the passable check.
### Minecraft Chat Apps
MCChat is ignoring teleports and setbacks coming from your server so you might get constant violation spam if you join with this application on your server together with NoCheatPlus. This issue can only get fully fixed by its developer itself.