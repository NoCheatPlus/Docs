Config path: `checks.moving.nofall`  
Permission (bypass): `nocheatplus.checks.moving.nofall`  
Exemption: `MOVING_NOFALL`  
Depends on: `[Moving] Survivalfly`  

This is a sub check of survivalfly, it makes sure that the player gets the damage he/she is supposed to get.

| Option              | Description |
| :------------------ | :---------- |
| dealdamage          | Override fall damage so NoCheatPlus handles it to prevent additional exploits. |
| resetonviolation    | Clean nofall data on attempts to take fall damage while not actually having hit the ground. |
| resetonteleport     | Compatibility fall-back option to clean nofall data after a teleport. |
| resetonvehicle      | Clean the nofall data after entering a vehicle. |
| anticriticals       | Prevent some critical exploits by resetting small amounts of fall-distance "in time". |

**Notes**
* resetonvehicle was set to true because of a strange bug that killed players when they left a vehicle.
* In Minecraft its possible to fake small amounts of fall damage to get fake critical hits on creatures/players. For that reason we highly recommend to let anticriticals to true unless you have no choice.


**Related**  
* [Active](Global#Active)
* [Actions](Global#Actions)
* [[Moving] Survivalfly](%5BMoving%5D-Survivalfly)
* [[Fight] Criticals](%5BFight%5D-Criticals)