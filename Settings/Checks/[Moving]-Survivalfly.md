Config path: `checks.moving.survivalfly`  
Permission (bypass): `nocheatplus.checks.moving.survivalfly`  
Exemption: `MOVING_SURVIVALFLY`  
Better with: `[Moving] Morepackets` and `[Combined] Bedleave`

SurvivalFly aims to control pretty much everything related to moving such as flying, running, swimming and more.

| Option                              | Description |
| :---------------------------------- | :---------- |
| extended _vertical-accounting_      | Monitor how the players speed varies in-air. Enforces gravity for a minimum amount. |
| stepheight                          | The height a player can from ground upwards to ground, without jumping. This is set to 'default' by default, so NCP will adjust it automatically with the Minecraft version. In case NCP can't detect the version properly, e.g. with custom builds, setting an explicit value might help. Used to be 0.5 before MC 1.8 and 0.6 from then on. |
| setbackpolicy _falldamage_          | Deal fall-damage according to fall-distance on survivalfly violations. Meant to make exploiting the set-back to last ground location more expensive. |
| setbackpolicy _voidtovoid_          | Attempt to set-back into the void, if already there. |
| hover _step_                        | Tick-period for which to perform hover checking. |
| hover _ticks_                       | Ticks after which a player is assumed to hover if still in-air and not moving. |
| hover _logingticks_                 | Extra ticks added to hoverticks directly after login, to give more leniency. Set this on problems with hover + loging in. |
| hover _falldamage_                  | Deal fall-damage according to fall-distance, to make avoiding fall-damage harder. |
| hover _sfviolation_                 | A hover violation is counted as a survivalfly violations with this amount of violation level. |
| leniency _hbufmax_ | The cap value for the horizontal buffer. Horizontal moving violations get compensated with emptying the buffer - it fills up with (allowed) moving below the applicable base moving speed (not accounting for special acceleration like with bunny hopping). |
| leniency _freezecount_ | The number of moves, for which the violation level can't decrease, after a violation has happened. |
| leniency _freezeinair_ | If set to true, the violation level can't decrease, while the player is moving in-air. 

The _leniency/freeze_ settings mainly aim at configurations that don't cancel for low violation levels. With the freezing option, cheaters can't create repeated small violations as easily.

There are also hidden options, which give more access to internals. Use with care, as these might allow different kinds of cheats or lead to other false positives, if changed. Ask back if in doubt or test changes made.

|Hidden Option                    | Description |
| :------------------------------ | :---------- |
| walkingspeed | Multiplier for the horizontal walking speed. Value is per-cent, 100 means no change (default), 200 doubles the allowed walking speed. Does not apply with sprinting! |
| sprintingspeed | Multiplier for the horizontal sprinting speed. Value is per-cent, 100 means no change (default) , 200 doubles the allowed sprinting speed. Does only apply with sprinting! Due to the sprinting state on server side not always reflecting the client side, NCP will assume the player to be sprinting whenever technically possible (setting: _assumesprint_) - this means that this setting will take effect when the player isn't too hungry. |
| blockingspeed | Multiplier for the horizontal walking speed, when blocking. Value is per-cent, 100 means no change (default), 200 doubles the allowed blocking speed. Overrides the modifiers above. |
| sneakingspeed | Multiplier for the horizontal walking speed, when sneaking. Value is per-cent, 100 means no change (default), 200 doubles the allowed sneaking speed. Overrides the modifiers above. |
| swimmingspeed | Multiplier for the horizontal swimming speed. Value is per-cent, 100 means no change (default), 200 doubles the allowed swimming speed. Overrides the modifiers above. |
| speedingspeed | Multiplier for the horizontal speed. Value is per-cent, 100 means no change, 200 doubles the allowed horizontal speed (default). This always applies extra to other modifiers, regardless of the side conditions, provided a player has the permission _nocheatplus.checks.moving.survivalfly.speeding_. |

**Notes**
* If you alter the actions in the configuration to not always cancel, you might be allowing glide-like cheats. Issues with horizontal speed are easier to work a around by configuration, than issues with the vertical part of a move (display [tags] for reference, ask back).
* A powerful tool for issues with moving is provided with the _on-the-fly debug logging feature_, significantly improving the odds for a quick fix: https://github.com/NoCheatPlus/Docs/wiki/Debugging#on-the-fly-debug-output-for-individual-players
* Hover is a sub-check of SurvivalFly which prevents players from hovering around in mid-air.

**Related**  
* [Active](General#Active)
* [Actions](General#Actions)
* [[Moving] Nofall](%5BMoving%5D-Nofall)
* [[Moving] Creativefly](%5BMoving%5D-Creativefly)