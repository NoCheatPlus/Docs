Config path: `checks.blockplace.speed`  
Permission: `nocheatplus.checks.blockplace.speed`  
Exemption: `BLOCKPLACE_SPEED`  

Prevents players from throwing projectiles (experience bottles, eggs, monster eggs, eyes of ender, ender pearls) really quickly in order to crash/lag the server.

| Option    | Description |
| :-------- | :---------- |
| interval  | The time (in milliseconds) between each thrown projectile. In theory it takes more than 150 ms if the player is keeping his/her right button pressed. |

**Notes**
* We set the default value to something lower then 150 ms in order to smooth out false positives that occur with latency

**Related**  
* [Active](General#Active)
* [Actions](General#Actions)