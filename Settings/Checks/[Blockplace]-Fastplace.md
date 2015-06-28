Config path: `checks.blockplace.fastplace`  
Permission: `nocheatplus.checks.blockplace.fastplace`  
Exemption: `BLOCKPLACE_FASTPLACE`  

Fastplace will prevent players from placing blocks too quickly by checking the interval of time elapsed since they've placed their last block. This should prevent players from using the features called "FastPlace" and "Build" of their modified client.

| Option             | Description |
| :--------------    | :---------- |
| limit              | Here you can set the maximal amount of blocks a player can place within 2 seconds. |
| shortterm _ticks_  | Set the amount of server ticks that Fastplace has to wait before it checks again in short term. |
| shortterm _limit_  | Set the maximal amount of blocks that a player is allowed to place in short term. |


**Related**
* [Active](General#Active)
* [Actions](General#Actions)