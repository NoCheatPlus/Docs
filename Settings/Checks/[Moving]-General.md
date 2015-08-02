This page explains configuration options which affect or support multiple moving checks.

| Option                          | Description |
| :------------------------------ | :---------- |
| trace _size_                    | |
| trace _mergedist_               | |
| vehicles _preventdestroyown_    | Prevent to destroy a vehicle while they are riding/mounting it.|
| vehicles _enforcelocation_      | |
| velocity _graceticks_           | |
| velocity _activationcounter_    | |
| velocity _activationticks_      | |
| velocity _strictinvalidation_   | |
| tempkickillegal                 | Setting this to false will just kick a player that does a illegal movement instead of actually tempbaning him for 24 hours. |
| loadchunks _join_               | Setting this to true will load up chunks around the player while he/she is logging in. |
| sprintinggrace                  | |
| assumesprint                    | Setting this to true will assume that the player is always sprinting. |
| speedgrace                      | |
| enforceloaction                 | |

**Notes**
* Players could do a illegal movements which would crash the server, so we made a check against it that would tempban a player for 24 hours if he/she exploits that. However some users wanted to just kick such players and for that reason we put boolean to activate/deactivate temporary banning called `tempkickillegal`.
* Minecraft fixed the "destroyown vehicle" bug so vehicles preventdestroyown option is just here for outdated servers but leaving it enabled wont conflict with anything either.
* The Minecraft client moves (well more falls) even if no chunks are loaded up which could trigger a tiny Passable false positive. We tried to smooth this further out by loading up the chuncks on join as fast as possible with `loadchuncks _join_`. It seems that Mojang allows the client to move inside unloaded chunks, for the vanilla fly check because it would prevent false positives with it.
* `assumesprint` has been implemented because the server doesnt always seem to tell properly if the client is sprinting now or not.
