# Installation
1. Download NoCheatPlus from one of those 2 sources:
 * Release builds on [DBO]
 * Latest development build on [Jenkins]

2. Drop the NoCheatPlus.jar in your /plugins folder like this:  ![Installation](Resources/Installation.gif)  

3. Start-up your server

# Configuration
1. [Make other plugins compatible with NoCheatPlus](Compatibility)
2. Install ProtocolLib to enable the NET checks
3. [Setup permissions](Permissions)
4. [Learn what YAML is and how to edit it](YAML)
5. [Configure NoCheatPlus](Configuration)
6. [Study the Commands](Commands)

[DBO]:http://dev.bukkit.org/bukkit-plugins/nocheatplus/files/
[Jenkins]:http://ci.md-5.net/job/NoCheatPlus/lastSuccessfulBuild/artifact/target/NoCheatPlus.jar

# Odds and Ends

There is a bunch of odds and ends to consider.
TODO: Formatting with secondary headlines etc., and links to existing pages for mentioned topics.

Noteworthy places where no configuration switch exists (only permission or exemption):
* TODO: Place boats onto something else but liquid.
* TODO: Place blocks against air or liquid.
* TODO: Details

Noteworthy checks/stuff for which no permission exists (config/exemption only):
* TODO: Details.

Noteworthy places where no exemption functionality is provided:
* TODO: Details

Noteworthy places where configuration is needed, extra to activating a feature:
* Untracked locations, abusing with commands: In order to prevent players abusing a special case in Spigot, to be able to teleport inside of blocks or bypass plugins that check for locations otherwise, currently NCP can only attempt to correct players positions at the moment they run a command.
 * TODO: Details for setting up the command prefixes for untracked teleporting (passable check).
 * TODO: This part is pretty important.
 * TODO: Fly by sethome?
* Piston support: Currently pistons are mostly unplayable with NCP on. Support is being implemented and reached a state where it might help with vertical pushing/pulling (since build 961, by far not finished).
 * TODO: Details how to a activate (set compatibility.blocks.changetracker.active to true).
* Command protection features
 * TODO: Details on what to add.
* TODO: Details

TODO: More details.
