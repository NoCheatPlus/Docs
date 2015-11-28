This page lists miscellaneous config options regarding fighting.

| Option                  | Description |
| :---------------------- | :---------- |
| canceldead              | Prevent dead players from hitting other players/creatures while being still dead. |
| toolchangepenalty       | Set the amount of time in milliseconds a player has to wait till he will be able to hit again after switching a item in his hotbar. |
| pvp _knockbackvelocity_ | You can define here if NoCheatPlus should calculate velocity by itself rather then using the velocity event of Bukkit. Set to true to enable, false to disable and default if you only want to enable it on Minecraft 1.8+ servers.|
| yawrate _active_        | Setting this to true will allow Yawrate to punish players for turning around too quickly while hitting (read more references) |

**Notes**
* canceldead is performing 100% silent without generation violations
* toolchangepenalty was a quick idea to limit AutoTool hack
* pvp _knockbackvelocity_ got implemented because the velocity event was giving out wrong data which caused false positives and other problems.

**Related**
* Violations
* [Combined] Yawrate
