TODO: Rename this page?

Future design questions/discussion/explanation. Some points are meant to be remembered, some are just there because someone can't sleep. 

Possibly top headlines should be ordered alphabetically? 


# Mostly decided

## More sensible penalties for fight checks

Having penalty time cancel all attacks clearly is problematic with false positives. It's been a technique to make auto-fighting less effective, e.g. after turning very fast, but it interferes too much with legit players.

More promising might be other approaches that don't necessarily prevent all fighting at once.
* Maintain some kind of "probability to cancel". Increase probability with violations.
* Prefer damage reduction over canceling (could randomize, which one to use).
* Do use damage reduction for criticals (maybe configurable which/what).
* Use a latency estimate and maintain a latency window for the location trace.
* Some pattern based detection might be interesting, later.

## Location trace with bounding box

The location traces (don't mix up with on-ground data stored for several moves) are meant for abuse tracking with targeting, and are also meant to be merged in some cases, in order to cover all time, distance, abuse. Due to that, it's probably best to also store the bounding box and keep extending the bounding box for an entry in case of merging.

## Passable (moving): adjust to client side

Y collision first, then x or z, then the remaining one (currently a workaround checks for y first, then xz in one go). Using the exact order which the client is also using, should reduce false positives further, be it configurable or not.

## Vertical friction issues

With vertical friction, moving out of water, usually the next move still has water friction, but it may happen that it's air friction. This is already an in-air move, but it might also happen on the second in-air move.

Solution:
* Track more fine grained on-ground/resetcond/etc. states with objects. Keep 3 moves at least. Such will allow simpler workarounds for a range of oddities and transitions. Uncertain: could track more than three, even on-demand.


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

## Global latency estimate

While this is somewhat difficult with networking and other congestion, not to mention server-side and client-side lag, it could be quite rewarding to track rough latency globally. 

* More latency sources can be used, e.g. outgoing keepalive packets, teleport-ack.
* A global latency estimate allows to be updated more than a check-specific one (...).
* With several latency-affected actions, one might spot inconsistent client behavior with cheating, e.g. fight checks with location trace vs. keepalive packets. If the client attempts to delay keepalive packets artificially, the broken order with vs. other packets might be detectable.
* With ANY latency window some sequences of actions can be checked for oddities, such as using velocity with odd delays , e.g. using glide-by-velocity.

Not sure if cheating with pistons will be popular soon, neither if they'll have pvp arenas with lots of pistons. Perhaps the cross-check usefulness is over-rated here (other than being updated by more sources)?

## Horizontal speeding

Counter measures:
* Confine bunny hop further. Find side conditions that can be added.
* Track the average speed per so and so seconds.
* Might attempt to detect sprint speed without sprinting. While server side sprint state can be inconsistent, there might be conditions with which to detect players, who should send a sprint start but don't. [Only useful, if that does something to the hunger level.]

Tracking the average speed mid-term seems quite promising, because it allows checking typical medium speed for ground+air and water+air and the like, limiting speeding for any medium[+air combination].

Technicalities:
* It would probably need tracking the allowed "normal" speed vs. the used speed.
* Friction envelopes after receiving velocity or switching state from somewhere (elytra, flying, whatever) need to be distinguishable from speeding.
** Probably already useful if we confine it only to the rough bunny envelopes (where we allow to move faster than normal without velocity).
** Tracking mid-term speed change by regarding shorter intervals will help to distinguish.
* Hard to tell where to set back to. Possibly needs keeping an extra mid-term set-back location like for morepakets, or we freeze the player in-place more or less.

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
** Train NCP to distinguish cheating from legit play.
** Use NCP to isolate patterns. Have NCP show for whom these patterns apply and when.
** Create interesting drawings from analyzing events for a cheat training session.
* Apart from in-game tools, also diagrams (of some type) could be translated into checks.
* Compile checks into (highly optimized) java code, at build time or even at runtime.

Examples:
* A meta check that combines several inputs to detect kill auras (e.g. fight checks vl, latency window shift events, lowjump events, pvp hit statistics).
* The "Toggle item/armor/sneak/block while moving" type of cheat.
