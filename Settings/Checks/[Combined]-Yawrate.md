Config path: `checks.combined.yawrate`  
Permission (bypass): `nocheatplus.checks.combined.yawrate`  
Exemption: `COMBINED_YAWRATE`  

This check keeps track of how fast players turned around and ensures it by monitoring movement and other actions like attacking. 
Yawrate will prevent players from attacking for a configurable penalty value (in milliseconds) if it catches a player turning around too much in a short time.

| Option             | Description |
| :----------------- | :---------- |
| rate               | Degrees per second in grad that a player is allowed to turn around without triggering a penalty. |
| penalty _factor_   | How many times should the counted penalties be multiplied? 2.0 is already double. |
| penalty _minimum_  | Set minimal amount of attacking penalty in milliseconds for every violation of Yawrate. |
| penalty _minimum_  | Set maximum amount of attacking penalty in milliseconds for every violation of Yawrate. |
| improbable         | Yawrate will integrate with improbable check if this is set to true. |

**Related**
* [Active](Global#Active)
* [Actions](Global#Actions)
* [[Combined] Improbable](%5BCombined%5D-Improbable)