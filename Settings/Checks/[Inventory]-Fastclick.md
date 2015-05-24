Config path: `checks.inventory.fastclick`  
Permission (bypass): `nocheatplus.checks.inventory.fastclick`  
Exemption: `INVENTORY_FASTCLICK`  

To prevent chest stealer's or auto armor hacks we simple limit the click speed a player is allowed to have while managing his/her inventory. 

| Option              | Description |
| :------------------ | :---------- |
| sparecreative       | Set this to true if you don't want Fastclick to check players that are in creative mode. |
| tweaks1_5           | Set this to true if you want to support the new inventory tweaks that were introduce in Minecraft 1.5 (such as inventory painting). |
| limit _shortterm_   | |
| limit _normal_      | |

**Notes**
* If you run Minecraft 1.4.x and older then set tweaks1_5 to false!
* This check will also prevent mods such as InvTweaks and similar ones from working right (because they give advantage compared to vanilla players), if you want your players to be able to use those mods then disable this check or give them the right exempt permission.

**Related**  
* [Active](Global#Active)
* [Actions](Global#Actions)
* [Long-term and Short-term](Backgrounds#long-term-and-short-term)