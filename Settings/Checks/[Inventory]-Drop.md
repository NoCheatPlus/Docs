Config path: `checks.inventory.drop`  
Permission (bypass): `nocheatplus.checks.inventory.drop`  
Exemption: `INVENTORY_DROP`  

Hackers can drop their entire inventory with 1 click to lag and crash your server, to prevent this we simply limit the amount of drops a player is allowed to do.

| Option              | Description |
| :------------------ | :---------- |
| limit               | Set the amount of items a player can drop in one timeframe. |
| timeframe           | Set the limit in ms (milliseconds) when the drop check should reset and start counting from scratch. |

**Notes**
* If (for example) your limit is set to 100 and your timeframe to 20, will allow your players to drop 100 items in 20 milliseconds

**Related**  
* [Active](Global#Active)
* [Actions](Global#Actions)