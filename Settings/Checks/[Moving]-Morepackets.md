Config path: `checks.moving.morepackets`  
Permission (bypass): `nocheatplus.checks.moving.morepackets`  
Exemption: `MOVING_MOREPACKETS`  
Better with: `[Moving] Survivalfly`

The Morepackets check is complementary to the Survivalfly and Creativefly checks. While the other check(s) limit the actual distance a player can move with one server-side event, this check limits the number of steps/events a player may perform within certain time-frames.

| Option                  | Description |
| :---------------------- | :---------- |
| seconds                 | The number of seconds to track. |
| epsideal                | The typical/ideal number of events per second, used for gaps. |
| epsmax                  | The maximum number of events per second tolerated (in average). |
| burst _packets_           | The number of events arriving within the first time window (currently half a second), to trigger increasing a (potentially excusable) burst event, e.g. with networking congestion. All packets above this count arriving within the same time window will increase the burst counting. |
| burst _directviolation_ | Amount of burst packets to trigger a violation directly, without even considering to calculate any mid-term average. With burst packets set to 40 and directviolation set to 60, more than 100 packets within the first time window will trigger the direct violation. This may seem much, but 5 seconds worth of lag happen more often than expected with the client side. |
| burst _epmviolation_     | Amount of burst events per minute to trigger a violation. Note that only bursts (...) get counted in here, as configured with burst.packets. |

**Notes**
* A normal value is 20 steps per second.

**Related**  
* [Active](Global#Active)
* [Actions](Global#Actions)