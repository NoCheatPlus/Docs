Config path: `checks.blockbreak.frequency`  
Permission (bypass): `nocheatplus.checks.blockbreak.frequency`  
Exemption: `BLOCKBREAK_FREQUENCY`  

Preventing players from breaking too many blocks in no time is the job of our Frequency check. It does not account for how fast an individual block can be broken, instead the frequency check just sets an upper limit to block breaking. This way creative mode and breaking blocks that can be broken "instantly" are limited to a reasonable frequency of breaking blocks.

| Option              | Description |
| :------------------ | :---------- |
| intervalcreative    | The minimally allowed time to pass between breaking blocks in creative gamemode. |
| intervalsurvival    | The minimally allowed time to pass between breaking blocks in survival gamemode. |
| shortterm _ticks_   | Number of server ticks (50 ms each) to keep track for limiting short term bursts. |
| shortterm _limit_   | Number of blocks to allow within the specified serverticks. |

**Notes**
* There is a general buffer counting in 2 seconds by default and allowing to accumulate as many blockbreaks as fit into the time given the intervalcreative and/or intervalsurvival settings interpreted as durations.
* In addition it has a short term setting, also counting the blocks within the last n ticks and limiting the short term amount. This way players cannot break 80 blocks at once and then pause for two seconds.

**Related**  
* [Active](Global#Active)
* [Actions](Global#Actions)