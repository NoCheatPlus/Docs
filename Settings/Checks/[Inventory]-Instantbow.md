Config path: `checks.inventory.instantbow`  
Permission (bypass): `nocheatplus.checks.inventory.instantbow`  
Exemption: `INVENTORY_INSTANTBOW`  

This check will make sure that your players use the proper fire speed to shoot arrows with a bow. InstantBow will take actions against players that try to go over the allowed limit.

| Option              | Description |
| :------------------ | :---------- |
| strict              | If set to true, this monitors time from pulling to firing. If set to false, this only regards the time between shots - use for problems with lag/latency, at the cost of allowing one instant shot. |
| delay               | |

**Related**  
* [Active](Global#Active)
* [Actions](Global#Actions)