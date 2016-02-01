TODO: Rename this page?

Future design questions/discussion/explanation. Some points are meant to be remembered, some are just there because someone can't sleep. 

Possibly top headlines should be ordered alphabetically? 


# Mostly decided

## Fight checks penalties

Implement penalties as an alternative to cancelling. This allows having less false positives, but also allows to have more strict limits, starting with penalties that only apply with a certain probability.

* Add a PenaltyAction like 'penalty:penaltyid'.
* Add a config section for penalties. e.g. 'penaltyid:dividedamage=1.5'.
* Alter Actions processing to handle cancel differently, so penalties are able to cancel too.
* Staged execution of penalties (Action.execute vs. context specific methods e.g. with using damage events).
* Now or later: Allow combining penalties 'a+b', allow first-match lists with probability to apply '50%devidedamage=2.0 -> 25%cancel -> attackert.ndt-5'.

## Redo LocationTrace

* Switch to expire by time instead of number of elements (except for extreme cases).
* Never merge entries with differing position, possibly not even if yaw/pitch differ.
* Might use MoveData.to/from directly (then with a global pool of objects).
* Include bounding box hints in the trace (width, height from PlayerLocation).

## Fight / loop checks (using LocationTrace)

* Distinguish pvp vs. pve settings, as the checks with trace allow much more precision.
* Possibly change implementation further, to be optimal for the loop checks (the first approach had been a quick adaption).
* Might already maintain a latency window/estimate.

## InteractRayTracing (blocinteract.visible)

* Switch to extend PassableRayTracing + maybe slight alterations.
* Possibly alter per-block ray check to use a real ray.
* Remove default exemption by flags configuration entries.
* Add examples to wiki.
* May add a named sets configuration for  (name -> active, flags, blocks) for doors and the like, disabled by default.

## Detect abusing vanilla fall damage

Clients can force vanilla fall damage by accumulating fall distance and faking the onground flag.

Thinkable solutions:
1. Check and correct the onground flag. [Problem: asynchronous handlers don't have Bukkit API access for blocks, plugins might change stuff on base of events.]
2. Always override the onground flag and let NCP deal with the effects. [Problem: Might change processing on server side, in terms of nasty side effects. Still might be feasible, if we can add-in a heuristic, e.g. updating a per-player block cache for off-primary thread access, or if there are no relevant side effects.]
3. Fall damage dealt by the server is mostly easy to detect, because it's not NCP dealing it, so it's possible to set-back in such a case. Of course there can be further checks:
 * Track repetition of letting Bukkit deal fall damage.
 * Track difference of height vs. accumulated fall distance.
 * Use tracked/queued flying packet data to check if the player is really on ground but told otherwise.
4. Cancel fall damage in such a case and undo effects.

3. and 4. look good and might give rise for further checks (detect accumulating fall damage using micro moves, e.g. inspecting flying packets).

## 1.9 support

### Let CreativeFly handle ELYTRA and LEVITATION

Alter CreativeFly to have more fine grained model configurations and triggers for when to use those.

New models configs will be referenced by name (currently the game mode is the key, which then will be the name).
* Key is just the name.
* Add an activation flag.
* Add a trigger entry.
* Distinguish h/v speed.
* Distinguish ascend and descend speeds.
* Add sprint modifiers for h/v.
* Flag for fall damage (levitation).
* Uncertain: Add a/the distance per move extra to or instead of the speed modifiers? Could relate all modifiers within a model node to the absolute reference speed within that node, or make the horizontal speed the absolute reference.

Conditions for triggers:
* Game mode.
* Potion effect.
* Armor item.
* Item in hand.
* (Item in inventory. For random jet pack support.)

Configuration/combination of triggers:
* Defined in one line.
* Conditions can be combined with 'and' and 'or', using '+' and ','.
* Example: iteminhand=END_ROD+chestplate=ELYTRA

### The usual stuff (block shape and breaking time support).

Start with something rough.

## Fight checks

### Criticals (Bukkit API)

The existing check should reduce the damage (1.5), instead cancelling. Possibly configurable.

### More sensible generic penalties for fight checks

Having penalty time hard-cancel all attacks clearly is problematic with false positives. It's been a technique to make auto-fighting less effective, e.g. after turning very fast, but it interferes too much with legit players.

More promising might be other approaches that don't necessarily prevent all fighting at once.
* Maintain some kind of "probability to cancel". Increase probability with violations.
* Prefer damage reduction over canceling (could randomize, which one to use).
* Do use damage reduction for criticals (maybe configurable which/what).
* Use a latency estimate and maintain a latency window for the location trace.
* Some pattern based detection might be interesting, later.

Penalties could consist of several types of penalties, which maintain a probability to apply with a maximum duration of validity.
* Types could be:
 * Cancel.
 * Cancel on keeping the target.
 * Cancel on switching the target.
 * Reduce resulting damage (somehow / depending on check specific settings).
 * Reduce nodamageticks (not sure this is such a good option for general penalties, but could be interesting on combined checks, considering players hitting a lot but not getting hit, despite pvp or what not).
 * Selective modifiers. E.g. some indicator to increase strictness for some other checks.
* Side conditions  / data / other conditions:
 * Time of expiration and creation time (the latter for tracking time running backwards).
 * Probability to apply (if the validity interval is extended, the resulting probability is somehow calculated, with remaining duration for previous expiration time and previous probability.).
 * Number of events to maximally apply the penalty for (until expiration, this might need being able to store multiple penalties per type).
 * Combined judgment + escalation mechanics. This could also be made "meta triggers", like increasing another probability thing if several others reach a certain level (planned in a generic way for later, but could be useful here too).
 * Could allow increasing probability for penalty type chosen at random.

Configuration complexity (penalties).
* Hard to imagine an elegant way to define all these things.
* Penalties could have ids likes strings and be defined in a special section or even a special configuration file (global only).
* Checks reference the penalty ids where appropriate (hard coded config path, or actions, like penalty:ridiculouspenalty). 

### Latency window

Fully implement maintaining a (possibly global/shared) latency window, making use of the full location trace, confining the timing window to consider further, shifting it by a maximum amount per attack (/tick?).

Having other inputs feed/alter the latency window might increase effectiveness.

Maintaining (short lived) location traces for other entities could be interesting too (reducing false positives, less coarse checking). Updating their traces would be done lazily on hitting (and then on tick, provided it's imperative to keep checking)

### More complex difficulty/targeting check

Estimate the difficulty of fighting/targeting and penalize too much success :p. Preferably be more accurate than the angle check.

Thinkable criteria:
* All that angle is using (switching looking direction, number of targets, moving).
* Make use of the moving traces of both attacker and attacked players/entities. Allows judging difficulty of targeting better.
* Balance false positives with detecting mobs confined into a narrow space (type of fight).
* Relate (average) moving speed to difficulty in general (mostly if the target is moving).
* Turning makes hitting harder in general (turning average amount and/or frequency...).
* Turning (rather quick) against the previous turning direction.
* Certain criteria rather from groups that multiply, as opposed to adding up.

### Detect type of fight

Detect types of fighting situations.
* Many entities around.
* Many entities within a small confined space.
* Players chasing each other. Might track allowed base-speeds vs. how the distances vary.)
* (Camping. The angle check penalizes camping).
* (Add real time comments, like with football manager games. Let mods vote on penalties.)

Initial focus would be detecting grinders and similar, in order to reduce false positives.

### Detect criticals on/with packet level

Monitor jumping/patterns and tip off the fight checks, so they can guess stuff (not entirely straight forward to get something better than just the pattern detection, because moving and fight events might be totally out of order or queued still, and the craftbukkit moving event threshold will also complicated things, could use mid-term probabilities).

#### Progress
A couple of past packets are kept in a list, so these could be used for checking in the primary thread, though it'd be good to be able to associate packets with moving events and the order of things.

### Location trace with bounding box

The location traces (don't mix up with on-ground data stored for several moves) are meant for abuse tracking with targeting, and are also meant to be merged in some cases, in order to cover all time, distance, abuse. Due to that, it's probably best to also store the bounding box and keep extending the bounding box for an entry in case of merging.

### Location trace time

An entry should probably always contain the creation time. The latest one always includes "now", and the following one shows the duration covered by its creation time. With iteration potentially going random directions with a latency window to maintain, one might also just store both creation and last update time.

### More coarse location trace

A location trace with lower resolution could be interesting, in order to track mid-term moving behavior. Could also be generated/updated on-demand, using the default trace as input. 

## Event frequency tracking, independent of an interval of time or buckets.

Add a data structure capable of detecting phases of similar frequency, having entries merged for similar frequency or if time to last event is within the merge interval, creating new entries for deviations. This way frequency tracking can have a custom resolution for time and amounts of tracked values, e.g. detecting low, mid, high, extreme amounts and (in theory) having an arbitrary span of time covered, capable of detecting low-frequency phases. Of course there should be some maximum amount of entries and a a merging policy (similar frequency of events, or event arriving within x milliseconds).

Thinkable variations: 
* Base: Add count/amount/1 to the latest entry, if arriving within so and so milliseconds. Otherwise leave a gap between (not sure if to add a gap entry to explicitly cover the count of zero, or to keep it implicit (or to add some field to an entry to cover the gap size to the previously added entry).
* Frequency: short-term track frequency (some time interval, some resolution), add the short term frequency every so and so.
* Multi-level: linking entries to another level of entries of more coarse resolution  (2d, time and resolution of merging entries).

Applications:
* Track mid to long term frequencies of events, check violations, other... for better judgment. 
* Detect phases of sending too few packets, e.g. for moving.
* Detect abuse of leniency towards client-side packet bursts.
* More precise counting in of server-side lag thinkable.
* Detect phases of similar speed. Helps with detecting speeding, judging pvp/chasing, other.

## Passable (moving): adjust to client side

Y collision first, then x or z, then the remaining one (currently a workaround checks for y first, then xz in one go). Using the exact order which the client is also using, should reduce false positives further, be it configurable or not.

In addition we could/should check that way using the full bounding box of the player, which is more simple due to regarding the move along one axis at a time.

## Track sequences of (continuous) violations.

Reduce false positives by tracking continuous violations.

* Mostly thought of for the survivalfly check, could also be useful for passable.
* Just set-back silently, without increasing the violation level, and without running all the violation handling. (Problematic might be that compatibility hooks can't help anymore in this case. Future design could do something about it.)
* Configuration:
 * Maximum number of subsequent violations to skip (including all and none, later possibly try a mixture of 'long' for teleport/login and latency estimate.).
 * Warning message for staff with a player being stuck in violations (message, count to activation, count/timing to repeat).


## Horizontal speeding

Counter measures:
* Confine bunny hop further. Find side conditions that can be (re-) added.
* Track the average speed per so and so seconds.
* Track bunny hop frequency.
* Might attempt to detect sprint speed without sprinting. While server side sprint state can be inconsistent, there might be conditions with which to detect players, who should send a sprint start but don't. [Only useful, if that does something to the hunger level.]

Tracking the average speed mid-term seems quite promising, because it allows checking typical medium speed for ground+air and water+air and the like, limiting speeding for any medium[+air combination].

Technicalities:
* It would probably need tracking the allowed "normal" speed vs. the used speed. Recording the ratio and number of events may be best, using ActionAccumulator. Resetting and skipping conditions might be intricate, thinking of the player sending small moves in-between [could give rise to using another data structure]. Tracking distance vs. real time is problematic, due to congestion/lag considerations. Having morepackets for that, we should have a good start on chases with going per-packet.
* Tracking the speed above average might be prone to false positives under some curcumstances, so some care is necessary (velocity, cascading in generic cases).
* Preventing the impact of false positives with tracking sequences of (continuous) violations, see above.
* Friction envelopes after receiving velocity or switching state from somewhere (elytra, flying, whatever) need to be distinguishable from speeding.
 * Probably already useful if we confine it only to the rough bunny envelopes (where we allow to move faster than normal without velocity).
 * Tracking mid-term speed change by regarding shorter intervals will help to distinguish.
* Hard to tell where to set back to. Possibly needs keeping an extra mid-term set-back location like for morepakets, or we freeze the player in-place more or less.

# Uncertain

## Abuse of vertical velocity

There are still cheats thinkable, similar to glide-by-velocity, stacking up velocity and using in a distinct way to glide/fly. While the new y-axis handling will prevent gliding endlessly with one time receiving velocity, you can still fill in vertical components for the received velocity (+- something).

Typically:
* Stack up velocity.
* Use selectively, leaving out unwanted amounts/directions.
* Maximize the delay between moves, before using the next velocity entry.
* Maximize horizontal speed.
* Minimize vertical speed.
* Possibly send fewer moving packets than usual.

Counter measures could include:
* Stricter horizontal velocity handling, similar to vertical velocity handling as is now (use once, friction in-air).
* Track unused velocity, detect selective use of positive / negative. Maybe a pattern engine, maybe just a counter/buffer thing.
* Minimizing vertical speed could also be detected like selective y-direction use.
* Do use latency estimates to check if the delays between moves somehow match the velocity use. Detect shifting the window all the time.
* Track sending too few packets.


## Block change tracking (pistons, redstone, digging, other).
To reduce false positives with pistons and to allow making doors much more safe we need to introduce some concept to track changed blocks and somehow account for them during all types of on-ground checking and passability checking, including ray-tracing.

What we might track:
* Pistons.
* Redstone changing blocks.
* Players digging.
* Plugins changing blocks.
* Blocks that are affected by gravity.

Key issues are:
* The old state of a changed block is what we need to track.
* The onground and passability checks need to be adapted to use the block change tracking.
* Redstone-driven changes may be itchy to follow. 
* Plugins changing blocks might not fire events.
* Need to keep an eye on abuse of redstone circuitry with pistons or doors.
* Prevent abuse of timing bounds.
* Prevent false positives with timing bounds.

### Already Implemented/Tested

#### Still simple: push entries up/down.

Pistons moving one time up might already be "ok", can't call that "playable" yet.

Pointers: 
* Even on a local test server the player would stand in-air on top of an already retracted block.

Conclusions:
* We do need on-ground tracking as well. Following problems:
 * Need to keep track of block shapes and data.
 * The state after having moved the block can't be known at the time of the piston event.
  * Queuing an update request for TickTask might be ok, as packets have to travel to the client anyway (could blow up on server side lag spikes).
  * Otherwise the state resulting of the piston event will be the one checked against first (it's 'actual'). Possibly no entries are needed, just states of all involved blocks at the time of the event.
 * The methods in BlockProperties that determine on-ground properties will lazily query data from BlockCache, thus we might need to implement BlockCache using the tracker, also considering the policy for a specific query (prefer blocks to be there or not, latency estimate).
  * Solution could be to always query data, thus add it as argument to all the methods. This will be simple but change many places.
  * Another Solution could be to change BlockCache to have one node-like entry per block, the node entry has access methods and keeps a reference of the block cache (...). Advantage being any past-state can be encapsulated somehow, this block state object will be passed to all the methods in BlockProperties instead of id/shape/data.

### Core data structures
A linked CoordMap variation will likely be used, in order to sort entries to front/back once updated, so periodic checking for expiration will be easy.

Inside such an entry/node, it'll probably simply be linked lists:
* Block tracking (shape, id, etc.). 
* Push tracking (for pistons, entry contains the direction, allow moving to the full block border by getting pushed, types for slime blocks vs. normal).

The push entries and the block entries will also have a time value and possibly a counter value, to be able to tell the order of events. Blocks might have a time-span of validity. Expiration starts for the previous state on changing it.

### Nature of queries to the tracking system

Queries for changed blocks might need to hint at the "desired" result, complicating things.

Example:
* The player wants to move in a legitimate way :), thus we need velocity or (with some more or less complicated query thing) we need to have touched ground somewhere.

Further we might encounter odd client behavior on edge cases, where we might have to check the last or second last move for if it has been on ground [heuristic estimation, not entirely sure]. Design-wise it would be interesting to be able to just re-run all checks over the last N moves on-demand. 

Another example:
* Think of the ground opening to let you fall into water instead of onto stone. [various ways our system could behave, depending on the implementation.]

With the last example, passable should allow the move (invalidating entries older than from retracting).


### Adjustments to passability checks and ray-tracing

Focus is "can the player move like this?", so we try to find a block configuration that works for the player to pass through. This dosn't seem to be particularly difficult, as we can just query the tracking system in case of a block colliding with the player.

### Adjustments to on-ground checks

This is slightly tricky, as we need an estimate if the move demands or might want to go onto ground (or otherwise have touched it). With a lot of random pistons, we could otherwise get an arbitrary result for checking the distance to ground (0, 1, 2, 3...). 

In essence, the player wants to be on ground usually where the x0,y1,y0 point is (vertical move only), but maybe the player doesn't want to be on ground there, if they are just falling. A latency estimate should be used, in order to be able to skip unwanted states. For a rather simple case, a too short move will either need velocity or moving onto ground (with uncertain margins).

### Abuse of latency 

For one thing the entry creation/update time and possibly a sequence number can be stored in the player data, so all older entries can't be used by the payer anymore.

Might try to maintain a global latency estimate + window mechanics and apply strictly. Server side lag and networking congestion complicate things.

For players "using" an already moved block too long, things may also get more complicated.

With high latency, players may have a couple of moves on a block just removed by a piston. The duration of allowing ground should not be (much) longer than the time until the block has been removed.

To keep the map size more confined, one could confine tracking to be near players, e.g. maintain tracked chunks, relate to if/how the player is moving.

### Initial minimum or pistons.

For starters we do need to make ordinary pistons work with survivalfly, at least vertically, because the new y-axis handling should prevent any move with pistons.

"Quick" approach:
* Implement per-world block change tracking for pistons only at first.
 * Track time+direction+id for the position of the end-block for extending pistons.
 * The id is an always increasing counter, player data contains a counter (and possibly a time), to be able to prevent using past entries.
 * Invalidation mechanics by time, use the LinkedCoordMap, use a mixture of lazy + TickTask.
 * Block Change entries contain a list with each extension for the piston (at least). Possibly the change direction is enough to know it's been a piston, the state of the block before extending needs to be present too.
 * Use the oldest block change entry for the player, preferably.
* For pistons: Allow moving to the edge of the block, at least vertically upwards.
 * Might want to check other conditions, full bounding box available.
 * Locations to check cover the whole bounding box (for the from location at least).
* Configurability if to use this feature at all, plus maybe max. age and number of entries.
* Not yet:
 * Maybe not yet horizontal, though that could be possible as well.
 * Full on-ground compatibility (jumping on shifty piston setups, no fall edge cases, possibly other).
 * Latency estimates.

### Initial minimum for non-pistons.

Maybe a quick thing for passable can be done here after doing the minimum for survivalfly.

* Trigger block change entries:
 * Moving onto a block or even having (to be added) flags present in the bounding box entries or along the move.
 * Maybe: Interaction with said types of blocks.
 * Maybe: redstone changing blocks (performance questions).
* Use the same block change infrastructure as for pistons, create entries with no direction (player is not going to get pushed).
* Add exemption for passable checking (passing block tracker as extra argument), possibly need a different return type there (AlmostBoolean?), or just risk some other tests for passability not using the block change tracking.
 * Passable ~ opportunistic version of the test: assume passing through is wanted, so look for states that allow it.
* Do remove config workarounds.
* Configurability if to use this sub-feature.
* Not yet:
 * Full NoFall compatibility.
 * Latency estimates.

## Global latency estimate

While this is somewhat difficult with networking and other congestion, not to mention server-side and client-side lag, it could be quite rewarding to track rough latency globally. 

* More latency sources can be used, e.g. outgoing keepalive packets, teleport-ack.
* A global latency estimate allows to be updated more than a check-specific one (...).
* With several latency-affected actions, one might spot inconsistent client behavior with cheating, e.g. fight checks with location trace vs. keepalive packets. If the client attempts to delay keepalive packets artificially, the broken order with vs. other packets might be detectable.
* With ANY latency window some sequences of actions can be checked for oddities, such as using velocity with odd delays , e.g. using glide-by-velocity.

Not sure if cheating with pistons will be popular soon, neither if they'll have pvp arenas with lots of pistons. Perhaps the cross-check usefulness is over-rated here (other than being updated by more sources)?

## Packet exploits (frequency)

Typically:
* Sending too few packets (potion saver).
* Sending too many packets (potion and fire remover).

Sending too many or too few packets of a type consistently should be detectable (sending too few is possibly easier to detect than sending too many).

## Event engine (meta checks, automata, patterns)

Combine basic triggers like check violations, in order to create new (meta-) checks. Adding all sorts of events or digested information as elementary inputs might also allow to run automata and perform some kind of pattern recognition. 

Basic technique:
* A check-building framework, set up by configuration.
* Combine check violations, all sorts of events and more or less digested data.
* Boolean algebra, arithmetics, etc. for combining input nodes.
*  
* Make vl escalation and cooldown/relaxing configurable for all checks and nodes.
* Actions and vl-thresholds will be defined within this system, then.

Basic motivation:
* Combine check violations to trigger meta checks.
* Better (or at least better configurable) versions of the "combined.improbable" type of checks.
* Spot simple patterns, that can't be obfuscated so easily. (Example: switch from armor to elytra to continue moving, most of the time, the armor is on.)

Future motivation:
* Detect certain cheats and clients by use of pattern recognition. Comparably easy to bypass, but disabling certain versions of cheats or even cheat clients, just by altering the configuration.
* Self-learning.
 * Train NCP to distinguish cheating from legit play.
 * Use NCP to isolate patterns. Have NCP show for whom these patterns apply and when.
 * Create interesting drawings from analyzing events for a cheat training session.
* Apart from in-game tools, also diagrams (of some type) could be translated into checks.
* Compile checks into (highly optimized) java code, at build time or even at runtime.

Examples:
* A meta check that combines several inputs to detect kill auras (e.g. fight checks vl, latency window shift events, lowjump events, pvp hit statistics).
* The "Toggle item/armor/sneak/block while moving" type of cheat.

## Cross plugin compatibility framework.

At least a generic thing should be built into NCP directly, without letting the build depend on other plugins. Allow other plugins to temporarily or permanently exempt players and other entities from checks, without having them buiild vs. NCP.

Could involve:
* Allow exempting players by means of attached metadata.
 * skipnocheat could be the key to start with.
 * Uncertain what is needed. The simple way is to just check if there is anything and exempt. More complex options might be to just exempt the next event of a certain type, or the duration of validity (tick, time, once, n times).
* Allow generic compatibility behavior for predefined event types (and other classes types, possibly players?).
 * Basic would be to define which check types to skip for that very event.
 * Advanced mechanics involve events that are induced by other events (e.g. a generic melee attack event will fire on damaging an entity with an attacker set, or a generic block break event will follow BlockDamageEvent.setInstaBreak).
 * Special cases might need reflection.
 * Confine by versions of other plugins (plugin-compatibility-behavior with id 123: using versions x...y of plugin Xyz).
* Allow to define behavior for Player instances that extend the NPC interface or have "npc" metadata set.
* Allow other generic (permanent/selective?) exemption methods (name of a player or UUIDs). 

## More developer friendly.

Big aim: get more devs on board.

High level aims:
* Make NCP more inviting towards developers.
* Make it possible to register a new check with one class.
* Make it possible to replace check implementations, add and remove listeners at runtime.
* Add a cross plugin compatibility framework to NCP.

Means:
* Add basic subsystems for a check broker framework. 
* More mod independent design. 
* More complex registry subsystem with dependency handling, auto registration once available, auto unregister once dependencies got removed.
* Dynamic check types (not an enum), generic config paths (and files) for checks.
* More flexible and more clear configuration system. Allow merge config and defaults into existing files, allow split into multiple files, allow folders for worlds, allow defining validity for multiple worlds within files, possibly more...
* Add basic providers for all sorts of core listeners/check pipelines, at least for Bukkit/Spigot.
* On the fly check adding and removal.
 * Needs internal listener registries, to allow reliably removing listener, also to allow reliable order of listeners.


## Generic mod support

Long term aim is to make NCP much more, if not completely mod-independent. Generic registries, generic data handling, generic config handling and dependency management (auto register once available) will allow us to add checks when necessary, replace checks where necessary. The upside also is, that we can easily replace subsystems for the case of some breaking changes. We don't need to support all versions of Minecraft, but usually many people stay on the previous version of Minecraft for a long time and we don't like to add branches for that.

## Towards side-effect-free check design

Especially complex checks like SurvivalFly keep altering all sorts of player data during checking. This is a problem, if we need to perform more heavy after-failure checks, complicating implementation of workarounds.

Pro:
* Checks can test various branches easily, without creating inconsistent data states.
 * Test with/without permissions.
 * On-ground judgment after failure: Standing on boats is rare, no need to always check, whenever a player is not standing on blocks.
 * On-ground judgment after failure: Test with accounting for recent map changes (pistons, building, explosions, etc.).
 * Test branches for assumptions made in the past (are we still within some assumed envelope, considering past N moves, if not continue like with resetting to now/some-time-then).
* Parts of the check are easier to exchange for alternate implementations.
* Data is altered on base of the actually used path of decision.
* Code might be easier to understand, having special case decisions queued as such, rather than handled implicitly.
* Potential for less programming errors (less side effects = easier predictability of code).

Con:
* Such is best decided before starting to implement the check. Could be complex/expensive to change to.
* Will lead to more object creation (not sure short living objects can be detected as such for such a complex check, though some objects can simply be stored and re-used).

Technically:
* More object oriented, at least more struct-like pieces of data, rather than endless amounts of flags in MovingData.
* Objects fit for remembering checking edge data for several moves.
* Objects for decisions: allowed speed, violation detected, workarounds applied. These allow keeping track of what workarounds are possible, having some type-like qualification for data, instead of a mere "distance above limit". This way after-failure checks can be much more streamlined for specific cases.
