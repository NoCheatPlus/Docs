Config path: `checks.moving.creativefly`  
Permission (bypass): `nocheatplus.checks.moving.creativefly`  
Exemption: `MOVING_CREATIVEFLY`  
Better with: `[Moving] Morepackets`  

This check limits the flying speed for players that are playing in creative and spectator gamemode.

| Option              | Description |
| :------------------ | :---------- |
| ignoreallowflight   | If set to true, players who are not flying but set to be _allowed to fly_ are still checked by the survivalfly check ~ expect minor set backs happening then. |
| ignorecreative      | Normally players in creative mode are checked by creativefly by default. Setting this to true will let NCP use survivalfly instead, unless for allow-flight or exemptions. |
| horizontalspeed     | Modifier for the maximally allowed horizontal speed. 100 means "normal" creative mode speed. 200 would be twice the speed. |
| maxheight           | This is a height limit which is counted from above the worlds maximum height (usually resulting in 256 + maxheight). |
| verticalspeed       | Modifier for the maximally allowed vertical speed. 100 means "normal" creative mode speed. 200 would be twice the speed. |

**Related**  
* [Active](Global#Active)
* [Actions](Global#Actions)
* [[Moving] Survivalfly](%5BMoving%5D-Survivalfly)