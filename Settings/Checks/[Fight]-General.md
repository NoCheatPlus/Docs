This page lists miscellaneous config options regarding fighting.

| Option                  | Description |
| :---------------------- | :---------- |
| canceldead              | Prevent dead players from hitting other players/entities while being still dead. This cancels silently.|
| toolchangepenalty       | Set the amount of time in milliseconds a player has to wait till he/she will be able to hit again after switching an item in his/her hotbar. Might limit AutoTool and similar by a little bit.|
| pvp _knockbackvelocity_ | Set if NoCheatPlus should assume velocity events to be broken, and adjust internals to cover up for false positives. Set to default, it will enable depending on the Minecraft version (currently: 1.8 and later). Force set with true/false.|
| yawrate _active_        | Yarate tracks how fast players turn sideways. Having yawrate enabled allows to prevent some types of actions such as turning instantly and hit another player or entity. Also feeds the improbable check.|

**Notes**
* pvp _knockbackvelocity_ has nothing to do with the already removed fight.knockback check.
**Related**
* Violations
* [Combined] Yawrate
