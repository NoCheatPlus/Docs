Config path: `checks.moving.passable`  
Permission (bypass): `nocheatplus.checks.moving.passable`  
Exemption: `MOVING_PASSABLE`  
Better with: `[Combined] Enderpearl`

Passable prevents moving into or inside of blocks (noclip).
| Option                                    | Description |
| :---------------------------------------- | :---------- |
| raytracing _active_                       | Activate ray-tracing to prevent to move past/through blocks. |
| raytracing blockchangeonly_               | Only perform ray-tracing for moving past block borders. More inaccurate, but faster in average. |
| untracked _teleport active_               | This is to prevent players setting home at or teleport to another player who is at an untracked location (currently only COMMAND teleport reason). Untracked locations exist due to CraftBukkit trying to be nice to plugins, by not firing events for moves that don't cover enough distance/turning, effectively allowing to shift a tiny bit into a block without plugins being able to notice in an effective way. |
| untracked _command active_                | NCP supports detecting potential abuse by detecting players running certain commands at untracked locations. Typically a cheater could try to move into a block just by a tiny bit, so plugins won't notice, then they'd set home there, move back the tiny bit and teleport into the other block in a 'legal' way. |
| untracked _command tryteleport_           | Control if NCP is only to warn, or to try to teleport the player to the last tracked position. |
| untracked _command prefixes_              | The commands to track. This should be all commands that let you set home/warp/back and similar locations you could teleport to. "warp" for example also includes "warp xyz ...". You can distinguish by using 'warp set' instead of covering unneeded commands with just 'warp', depends on the plugins/command syntax. |

**Notes**
- Passable accounts for the foot position, not for the whole bounds of the player.
- Some blocks changing shape with redstone current are exempted from passable by default, in order to make them playable for higher latency players. You can remove those exceptions from the configuration under _compatibility.blocks.ignorepassable_ . 
- Violations might also trigger if players teleport or join and start moving while not having received or rendered the chunk they stand on. This causes the client to think that there are only air blocks around so it "falls down" and accidently clips a little into the solid blocks on your server. So please DO NOT quickly ban on Passable violations!
- The more lag, the more time it takes for the world to load up and the more likely it is for Passable to throw a false positive on join/teleport.

**Related**  
* [Active](General#Active)
* [Actions](General#Actions)
