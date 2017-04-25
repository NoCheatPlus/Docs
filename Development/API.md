# History of API changes
* Not sure we can keep double-bookkeeping here.

# Official API
The static access starting point can be: `NCPAPIProvider.getNocheatPlusAPI()`

This is largely incomplete, but contains some useful functionality, such as getting handles for registrations with the IGenericInstanceRegistry.

# Hooking into NoCheatPlus
The hooks package of NCPCore contains two "managers" for different concepts to exempt players from checks.

`NCPExemptionManager` This is the simple way to just exempt a player from a check, then unexempt. The current implementation is meant to be used short-term rather. Different plugins using exemptions might easily conflict. There is a command to set exemptions manually as well (useful for faster testing). If a player is exempted from a check, the check will not be run at all (for virtually all cases).

`NCPHookManager` This allows to register "hooks" that get called in case of violations and allow to do more complex stuff ("after-failure" hooks: the check is run). Hooks are able to prevent further actions processing, you can also register "stats" hooks that come first or force your hook to be registered before other hooks by implementing an extra interface. Cancelling the actions processing will not reset violation levels(!). For some cases you can reset them manually, though that is not officially supported yet (Example: MovingData.getData(player).clearFlyData() ...clearMorePacketsData() ...survivalFlyVL = 0).

Moving/flying skills might work with adding velocity to the player - if not, please provide us with a moving trace. Link Debugging Page here.
 
# Other hooking spots
There are more spots that are accessible, but most are "not officially supported", such as `ConfigurationManager`, `DataManager` and `ExecutionHistory`. Some are designs of older times, some are more like refactoring stages (probably stuck in it slightly).

Some methods of the TickTask (utilities) might be useful. 

Reloading the configuration can also be registered for:
* NCPReloadEvent (commands.CommandHandler). Called after reload done.
* You can register a component implementing INotifyReload (commands) to receive word of reloading the config just before the event is fired. This is also used by some checks and other components of NCP. These are cleared on reloading.

The plugin class itself does have some methods some of which could be of use, however we prefer you to use NCPAPIProvider.getNoCheatPlusAPI(), since we might separate some API from the plugin class itself, keeping the static API provider as long as possible (since 3.9.2-RC-b520 some static API has been moved to not-static, still implemented in the plugin class, should use NoCheatPlusAPI, though).

# Examples

## Adjusting the set-back location.
Until it's supported or not necessary to be done externally anymore, have a look here: https://gist.github.com/asofold/b05c0a17c605e7c69bb30ee5e79a6e7b

(The most important part is not to set back into blocks, and to not use the second part of a split move for reference.)

# Related
* [Debugging](Debugging)
