Config path: `checks.moving.creativefly`  
Permission (bypass): `nocheatplus.checks.moving.creativefly`  
Exemption: `MOVING_CREATIVEFLY`  
Better with: `[Moving] Morepackets`  

This check limits the flying speed for players that are playing in creative and spectator gamemode.

Provided the creativefly check is activated at all, the following conditions can force use of the creativefly check, regardless of options 'ignoreallowflight' and 'ignorecreative'
* The survivalfly check is not activated for the player (activation, exemption, permissions).
* The player is flying.
* The player is gliding with an elytra.
* The player is exposed to the levitation effect.

| Option              | Description |
| :------------------ | :---------- |
| ignoreallowflight   | If set to false, the creativefly check will run for players who are set to be _allowed to fly_. If set to true, the survivalfly check will be run instead, provided there are not other side conditions forcing use of the creativefly check. This does not disable the creativefly check. |
| ignorecreative      | If set to false, the creativefly check will run for players who are in the _creative_ game mode, regardless if they're flying or not. If set to true, the survivalfly check will run instead, provided there are not other side conditions forcing use of the creativefly check. This does not disable the creativefly check. |
| horizontalspeed     | Modifier for the maximally allowed horizontal speed. 100 means "normal" creative mode speed. 200 would be twice the speed. |
| maxheight           | This is a height limit which is counted from above the worlds maximum height (usually resulting in 256 + maxheight). |
| verticalspeed       | Modifier for the maximally allowed vertical speed. 100 means "normal" creative mode speed. 200 would be twice the speed. |

**Related**  
* [Active](General#Active)
* [Actions](General#Actions)
* [[Moving] Survivalfly](%5BMoving%5D-Survivalfly)