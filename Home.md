_nDcos 0.5 for NoCheatPlus 853_
![Title](https://raw.githubusercontent.com/asofold/NCPDocs/master/wiki/resources/sNCPBanner.gif)

Welcome to the wiki! This page will explain everything that you need to know about NoCheatPlus.

NoCheatPlus is a Bukkit (CraftBukkit/Spigot) plugin meant to protect your server from various kinds of cheating. A wide area of cheats is covered, such as player and vehicle moving, interaction, block breaking and placing, fighting, chat and other types of areas including client behavior that might crash the server.

The fundamental concept of NoCheatPlus is to cover the most important grounds for survival game play with _deterministic protection_ in the first place. This means the protection is meant to still be there after cheat clients have updated, and it can only by bypassed if there are bugs. Naturally not all possible cheats are covered or are even possible to cover, and cheat clients can adapt to the limits in some cases, but they can't _break_ the limits.

The next layer consists of _heuristics and educated guessing_, which may be more prone to allow actual bypasses, but which are likely to hold for a while, due to the conception aiming at fundamental mechanics of legitimate game play rather than detecting specific behavior of cheating, the latter of which could change with a cheat client update.

The thing we do least is _detecting specific cheats or patterns of cheating_, which allow the cheat client to update and completely bypass the checks, in which case we would end up with _hourly updates_ on both sides. Such an approach would allow for easier banning, however despite the _detection_ for a range of known cheats and cheat clients, it does not provide any actual long-term _protection_, which is why we don't rely on such methods in the first place.

The default configuration doesn't necessarily fit all types of game-play same way, luckily you can adjust it to your needs. Check parameters and actions allow to adjust the sensitivity for both preventing what players attempt to do and for logging alerts. It is possible to deactivate checks or to just have NoCheatPlus log alerts.

To get started follow those instructions: [Getting Started](Getting-Started)

Quickly find the appropriate build for a version of Minecraft: [Notable Builds](Notable-Builds)

Report an issue, or request support: [Issues](https://github.com/NoCheatPlus/Issues/issues)

If you need a full index search on this wiki, have a look at: [Github Wiki Search](https://github.com/linyows/github-wiki-search) 

