Config path: `checks.blockinteract.direction`  
Permission (bypass): `nocheatplus.checks.blockinteract.direction`  
Exemption: `BLOCKINTERACT_DIRECTION`  

The Direction check forces players to look (eye location) at the block they want to interact with.

**Notes**
* The BukkitAPI throws a interaction event before the place/break events come, so the BLOCKINTERACT_DIRECTION check will pretty much always catch the cheat attempt first before the other 2 do. If you wish to only check Direction on placing/breaking then disable the interaction one first.

**Related**  
* [Active](General#Active)
* [Actions](General#Actions)