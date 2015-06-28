Config path: `checks.blockinteract.speed`  
Permissions: `nocheatplus.checks.blockinteract.speed`  
Exemption: `BLOCKINTERACT_SPEED`  

The speed check limits the amount of interactions a player can do within a given time frame. It was originally developed to prevent spam on blocks like noteblocks which could even crash clients with bad hardware.

| Option    | Description |
| :-------- | :---------- |
| interval  | Interval in ms (milliseconds) for how long the speed check will keep the counted data before starting from 0 again. |
| limit     | Maximal amount of interactions that can be done in that given interval |

**Notes**
* Be aware that its possible to do 20-30 interactions in 2 seconds even without a modified client
* Trying to constantly break grass in a protected area (WorldGuard) can create about 35-45 interactions in 2 seconds.

**Related**
* [Active](General#Active)
* [Actions](General#Actions)