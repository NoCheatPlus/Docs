Config path: `checks.moving.survivalfly`  
Permission (bypass): `nocheatplus.checks.moving.survivalfly`  
Exemption: `MOVING_SURVIVALFLY`  
Better with: `[Moving] Morepackets` and `[Combined] Bedleave`

SurvivalFly aims to control pretty much everything related to moving such as flying, running, swimming and more.

| Option                              | Description |
| :---------------------------------- | :---------- |
| extended _vertical-accounting_      | Monitor how the players speed varies in-air. Enforces gravity for a minimum amount. |
| falldamage                          | Deal fall-damage according to fall-distance on survivalfly violations. Meant to make exploiting the set-back to last ground location more expensive. |
| hover _step_                        | Tick-period for which to perform hover checking. |
| hover _ticks_                       | Ticks after which a player is assumed to hover if still in-air and not moving. |
| hover _logingticks_                 | Extra ticks added to hoverticks directly after login, to give more leniency. Set this on problems with hover + loging in. |
| hover _falldamage_                  | Deal fall-damage according to fall-distance, to make avoiding fall-damage harder. |
| hover _sfviolation_                 | A hover violation is counted as a survivalfly violations with this amount of violation level. |

**Notes**
* Hover is a sub-check of SurvivalFly which prevents players from hovering around in mid-air.

**Related**  
* [Active](General#Active)
* [Actions](General#Actions)
* [[Moving] Nofall](%5BMoving%5D-Nofall)
* [[Moving] Creativefly](%5BMoving%5D-Creativefly)