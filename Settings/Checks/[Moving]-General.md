This page lists configuration options which affect or support multiple moving checks.

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
| tempkickillegal                 | Setting this to false will just kick a player that does a illegal moving instead of tempban him for 24 hours. |
| loadchunks _join_               | |
| sprintinggrace                  | |
| assumesprint                    | |
| speedgrace                      | |
| enforceloaction                 | |

**Notes**
* Players could do a illegal move which would crash the server so we made a check against it that would tempban a player for 24 hours if he/she tries that. However some users wanted to just kick such players and for that reason we put in a boolean to activate/deactivate temporary banning with "tempkickillegal".
* Minecraft fixed the "destroyown vehicle" bug so vehicles preventdestroyown option is just here for outdated servers but leaving it enabled wont conflict with anything either.