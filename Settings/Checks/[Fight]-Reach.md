Config path: `checks.fight.reach`  
Permission (bypass): `nocheatplus.checks.fight.reach`  
Exemption: `FIGHT_REACH`  

Players may slightly increase the distance at which they can attack enemy creatures/players. This check will try to identify that by comparing the distance between player and target location.

| Option              | Description |
| :------------------ | :---------- |
| survivaldistance    | Maximum attack distance for survival and adventure gamemode. Statically about 3 or 3.5 applies, with latency and moving 4.5 makes sense. |
| penalty             | Extra attack penalty for close combat, dealt on violations. |
| reduce              | Enable/disable the dynamic max-distance feature: If players hit rather at the limit of distance, the dynamic maximum is reduced, so it is harder to use kill-aura. A player that hits between dynamic max and max distance gets a "silent cancel" without violation level added. |
| reducedistance      | Maximum amount of distance by which the max-distance (survivaldistance) can be reduced. |
| reducestep          | Amount to change the dynamic max-distance per long-distance or short-distance hit. |

**Notes**
* Because of lag the reach distance isn't a fixed value and may increase/decrease, reach is for that reason designed to be dynamic and adapt to server lag if needed.

**Related**  
* [Active](General#Active)
* [Actions](General#Actions)