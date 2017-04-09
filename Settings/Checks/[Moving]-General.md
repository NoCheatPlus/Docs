This page explains configuration options which affect or support multiple moving checks.

| Option                          | Description |
| :------------------------------ | :---------- |
| trace _size_                    | Number of entries in the per-player location trace.|
| trace _mergedist_               | Exceeding this distance with a move means that a new entry is created, otherwise it'll be merged into the latest one.|
| vehicles _preventdestroyown_    | Prevent to destroy a vehicle while they are riding/mounting it.|
| vehicles _enforcelocation_      | Attempt to track extreme deviations from the vehicle position and correct them. Experimental (hopefully-) legacy option. Likely inoperable and useless, subject to removal.|
| velocity _activationcounter_    | Queued unused velocity is removed after this amount of incoming moving packets.|
| velocity _activationticks_      | Queued unused velocity is removed after this amount of server ticks.|
| velocity _strictinvalidation_   | More strict invalidation of queued velocity. Might get removed.|
| ignorestance | Ignore the bounding box check for players. This can be used to prevent compatibility issues on legacy setups. Set to default, it will disable from 1.8 on. Force set with true/false. |
| tempkickillegal                 | Setting this to false will just kick a player that does a illegal movement instead of actually tempbanning him for 24 hours. Technically NCP uses its deny login feature, only counting until next restart, not the ban command.|
| loadchunks _join_               | Setting this to true will load up chunks around the player while they are logging in. |
| sprintinggrace                  | Grace-period in seconds for sprinting. Due to latency, there are often still moves incoming, after ther server-side has caused sprinting to expire/toggle.|
| assumesprint                    | Setting this to true will assume that the player is always sprinting. The server-side state does not always match what the client does.|
| speedgrace                      | Grace-period in seconds for speed potion. Same as with sprintinggrace, the server might remove the potion effect and there are still moves incoming due to latency.|
| enforcelocation                 | Track if the player has somehow managed to get to ridiculous places without a moving event firing. Fixed the vehicle-teleport exploit. Legacy option for some time before Spigot 1.7.10. Setting to default will activate/deactivate based on the detected Minecraft version. Force set with true/false.|

There are also hidden options, which give more access to internals. Use with care, as these might allow different kinds of cheats or lead to other false positives, if changed. Ask back if in doubt or test changes made.

|Hidden Option                    | Description |
| :------------------------------ | :---------- |
| yonground                       | Control the vertical distance to blocks, at which NCP will assume the player to touch ground. This affect any moving-related checks, dealing fall damage etc. Capped at a maximum value of 0.0625, and a minimum of 0.00001. The default value may be around 0.016. Adjusting this to something higher might allow moving slightly above cactus without taking damage, but it might also help on certain false positives. Changes should be tested with issues that can be reproduced at will. |
| setback _method_                | Technique of setting back players. Legacy before MC 1.9: "set_to" The set_to setting will lead to problems since MC 1.11.2 since 2017-03-24, because TeleportCause.PLUGIN will result there, leaving potential for misinterpretation by other plugins. For MC 1.11.2 but also for 1.9 and later, the setting "cancel+update_from+schedule" is the default, itwould cancel moving events, and induce teleporting to the set back location by updating the from location, with a fall-back check on-tick (schedule). |

**Notes**
* Players could do a illegal movements which would crash the server, so we made a check against it that would tempban a player for 24 hours if they exploit that. However some users wanted to just kick such players and for that reason we put boolean to activate/deactivate temporary banning called `tempkickillegal`.
* Minecraft fixed the "destroyown vehicle" bug so vehicles preventdestroyown option is just here for legacy servers. Leaving it enabled won't conflict with anything either.
* The Minecraft client moves (well more falls) even if no chunks are loaded up which could trigger a tiny Passable false positive. We tried to smooth this further out by loading up the chuncks on join as fast as possible with `loadchuncks _join_`. It seems that Mojang allows the client to move inside unloaded chunks, for the vanilla fly check because it would prevent false positives with it.
