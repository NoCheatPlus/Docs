# History of API changes
* Not sure we can keep double-bookkeeping here.

# Maven


Repositories:
```xml
    <repository>
      <id>md_5-snapshots</id>
      <url>https://repo.md-5.net/content/repositories/snapshots/</url>
    </repository>
    <repository>
      <id>md_5-releases</id>
      <url>https://repo.md-5.net/content/repositories/releases/</url>
    </repository>
```

Depend on NoCheatPlus (snapshot):
```xml 
   <dependency>
    <groupId>fr.neatmonster</groupId>
    <artifactId>nocheatplus</artifactId>
    <version>3.16.1-SNAPSHOT</version>
    <scope>provided</scope>
   </dependency>
```

# Official API
The static access starting point can be: `NCPAPIProvider.getNocheatPlusAPI()`

This is largely incomplete, but contains some useful functionality, such as getting handles for registrations with the IGenericInstanceRegistry.

# Hooking into NoCheatPlus
The hooks package of NCPCore contains two "managers" for different concepts to exempt players from checks.

`NCPExemptionManager` This is the simple way to just exempt a player from a check, then unexempt. The current implementation is meant to be used short-term rather. Different plugins using exemptions might easily conflict. There is a command to set exemptions manually as well (useful for faster testing). If a player is exempted from a check, the check will not be run at all (for virtually all cases).

`NCPHookManager` This allows to register "hooks" that get called in case of violations and allow to do more complex stuff ("after-failure" hooks: the check is run). Hooks are able to prevent further actions processing, you can also register "stats" hooks that come first or force your hook to be registered before other hooks by implementing an extra interface. Cancelling the actions processing will not reset violation levels(!). For some cases you can reset them manually, though that is not officially supported yet (Example: MovingData.getData(player).clearFlyData() ...clearMorePacketsData() ...survivalFlyVL = 0).

**Moving/flying skills** might work with adding velocity to the player (MovingData) - if not, please provide us with a [debug log](Debugging). Vertical velocity currently supports a few flags (fr.neatmonster.nocheatplus.checks.moving.velocity.VelocityFlags) - this may be extended to control automatic velocity removal better (flags to retain entries, flags for horizontal velocity).

**Event handlers relating to listeners of NoCheatPlus:** Register listeners with the NoCheatPlusAPI, relating to sorting order.
* NoCheatPlusAPI.addComponent(Bukkit Listener) or NoCheatPlusAPI.getEventRegistry() to add an efficient MiniListener.
* Use @RegisterMethodWithOrder for per-method registration order with Bukkit Listeners.
* Use @RegisterEventsWithOrder for a preset for all event handlers contained in the listener.
* Pass a RegistrationOrder instance directly to the event registry to have a preset.
* Implement IRegisterWithOrder with a MiniListener. (@RegisterWithOrder is also supported for MiniListener instances, for obscure reason.).
* (Note 1: MiniListener instances only have one event handler method.)
* (Note 2: Currently the tags for listeners within NCP are not fully set up - check listeners should have something with NoCheatPlus inside. Priority values have not been considered yet either. This will soon receive an overhaul, so you can distinguish between feature and system listeners, e.g. to have data adjusted before wrapping around actual check listeners.)

# Other hooking spots
There are more spots that are accessible, but most are "not officially supported", such as `ConfigurationManager`, `DataManager` and `ExecutionHistory`. Some are designs of older times, some are more like refactoring stages (probably stuck in it slightly).

Some methods of the TickTask (utilities) might be useful. 

Reloading the configuration can also be registered for:
* NCPReloadEvent (commands.CommandHandler). Called after reload done.
* You can register a component implementing INotifyReload (commands) to receive word of reloading the config just before the event is fired. This is also used by some checks and other components of NCP. These are cleared on reloading.

The plugin class itself does have some methods some of which could be of use, however we prefer you to use NCPAPIProvider.getNoCheatPlusAPI(), since we might separate some API from the plugin class itself, keeping the static API provider as long as possible (since 3.9.2-RC-b520 some static API has been moved to not-static, still implemented in the plugin class, should use NoCheatPlusAPI, though).

# Examples

## Adjusting the set-back location.
Essentially MovingData.setTeleported from within a hook does the job - it will be handled as the location to set "back" to, only do this if IViolationData.willCancel() returns true, otherwise nothing else should be done, except perhaps to ensure not to let players collide with or pass through blocks with this (and don't allow flying, ...).

Notes from the past with some potentially useful details (note that some points are not up to date anymore): https://gist.github.com/asofold/b05c0a17c605e7c69bb30ee5e79a6e7b


# Related
* [Debugging](Debugging)
