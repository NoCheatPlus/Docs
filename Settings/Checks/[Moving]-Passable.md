Config path: `checks.moving.passable`  
Permission (bypass): `nocheatplus.checks.moving.passable`  
Exemption: `MOVING_PASSABLE`  
Better with: `[Combined] Enderpearl`

Passable prevents moving into or inside of blocks (noclip).

| Option                                    | Description |
| :---------------------------------------- | :---------- |
| raytracing _active_                       | Activate ray-tracing to prevent to move past/through blocks. |
| raytracing blockchangeonly_               | Only perform ray-tracing for moving past block borders. More inaccurate, but faster in average. |
| untracked _teleport active_               | Set to false if you want to check players with Passable even while they are teleporting. |
| untracked _command active_                | Set this to false to disable the command tracking feature of Passable. |
| untracked _command tryteleport_           | "tryteleport" tries to narrow down commands that do some kind of teleportation to smooth them out too. |
| untracked _command prefixes_              | If "tryteleport" fails you can list command prefixes here to let Passable support them. " - setback" for example also includes " - setback 1234" or "setback jkj 1234". |

**Notes**
- It might also trigger if players teleport or join and start moving while not having received or rendered the chunk they stand on. This causes the client to think that there are only air blocks around so it "falls down" and accidently clips a little into the solid blocks on your server. So please DO NOT quickly ban on Passable violations! Also enable untracked teleportation to smooth out false positives on teleports.
- The more lag, the more time it takes for the world to load up and the more likely it is for Passable to thorw a false positive on join/teleport

**Related**  
* [Active](General#Active)
* [Actions](General#Actions)
