Config path: `checks.moving.passable`  
Permission (bypass): `nocheatplus.checks.moving.passable`  
Exemption: `MOVING_PASSABLE`  
Better with: `[Combined] Enderpearl`

Passable prevents moving into or inside of blocks (noclip).

| Option                                    | Description |
| :---------------------------------------- | :---------- |
| raytracing _acrive_                       | Activate ray-tracing to prevent to move past/through blocks. |
| raytracing blockchangeonly_               | Only perform ray-tracing for moving past block borders. More inaccurate, but faster in average. |
| actions _active_                          | |
| actions _tryteleport_                     | |
| actions _prefixes_                        | |

**Notes**
- It might also trigger if players teleport or join and start sending moving events while not having received or rendered the chunk they stand on. Yet the player assumes to be falling and communicates that to the server, NCP will see them moving into blocks - so no quick banning on these!

**Related**  
* [Active](Global#Active)
* [Actions](Global#Actions)