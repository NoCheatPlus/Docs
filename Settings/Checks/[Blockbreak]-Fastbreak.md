Config path: `checks.blockbreak.fastbreak`  
Permission (bypass): `nocheatplus.checks.blockbreak.fastbreak`  
Exemption: `BLOCKBREAK_FASTBREAK`  

Fastbreak forces players to break blocks with realistic speed when being in survival gamemode. In order to smooth out lag spikes we allow a tiny bit of faster block breaking times to avoid false positives when server or client encounter latency (be it network or CPU time-outs). 

| Option           | Description |
| :--------------- | :---------- |
| strict           | If set to true, fastbreak will measure the time from interaction to block break. If set to false, it will measure the time from block break to block break, which allows one cheated fast break always, but forces normal speed for sequences of block breaks, being less strict in laggy environments, or in case the server mod does the interact events differently. |
| delay            | Here you can give a little bit of additional per block breaking time in order to avoid false positives when events get delayed by the server tick. NoCheatPlus reads this value in milliseconds (ms). |
| intervalsurvival | Modifier in % for block breaking duration in survival mode. Set to a lower value to allow faster block breaking (in per cent). |
| grace            | Set a value in milliseconds (ms) that players will be allowed to mine faster in each check period of fastbreak. |

**Notes**
* Blocks with a low breaking time could allow instant breaking if [their breaking time - set delay] results in a small value
* Fastbreak combines with the frequency check: the latter will hard-limit the number of blocks regardless of type, which is important if the fastbreak check allows "instant" breaking.
* Do not set intervalsurvival to something higher then 100% or all block breaking is likely to become violations.

**Related**  
* [Active](Global#Active)
* [Actions](Global#Actions)
* [[Blockbreak] Frequency](%5BBlockbreak%5D-Frequency)