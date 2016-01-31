# Using fake entities to detect fight-cheats

## Idea
* Fake entities are placed and moved around near players.
* Legitimate players are not meant to notice the fake entities in any way.
* A cheat implementation might take them for real and attack them.

### Preventing false positives
* Entities might be rendered invisible.
* Render so shortly that players don't notice.
* Moving entities around, such that the legitimate player never is able to hit them.
* Tricks.

### Make the entities appear real to the cheat implementation
* Render invisible.
* Adjust field of view.
* More tricks.

### Expected benefit of the method
* Cheaters are detected almost 100% of the time.
* False positives hardly exist.
* Banning (almost) instantly is possible.
* Positive PR due to banning real cheaters.
* Performance impact is low, due to only using packet sending for faking entities, possibly run asynchronously.

## Problems
Current known issues are:
* Interference with game play: flickering, false positives due to latency (after all something clickable is clickable).
* Easily detectable: Even without using cheats, the use of this method is certainly detectable with quite simple code. Clients could adjust on-the-fly, at least not to get banned.
* Clients can emulate normal clicking. The code is on client side, it's certainly possible to just have the cheat use the vanilla code for estimating what is hit, instead of sending an attack packet for a nearby entity.
* It's unthinkable that players can't see entities, but a cheat running on client code can't determine what's rendered/visible.
* Same goes for bounding boxes: If a player can't click on it, why should a cheat client click on it?
* If the entities are changed such that there is only a very short window to hit an entity with a certain id, you could have a legitimate player still click on it due to latency/congestion, and you will have cheat implementations that just queue the necessary actions and play them out realistically, including emulating clicking like a player.
* Bypasses: Claims are bypasses exist. Very likely, and very likely it'll be bypassed in generic ways, so it won't really pay to use fake entities for direct detection at all.
* You can reduce false positives by having thresholds, demanding multiple hits.
 * A player with networking congestion could still see a 1-tick-visible thing and run in circles and keep hitting it for 1 or 2 seconds, despite it being very improbable. This needn't be a problem, however how does the player explain not to have used cheats?
 * This doesn't really affect the general problems with the clients being able to bypass it.

## Outlook
* What a player can click on a client can click on too. A client may not want to click on things players can't click on. A client may not want to pursue targets that haven't been rendered.
* Only simplistic/old-style clients are caught. Better than nothing (see conclusion).
* Obfuscating real players and entities in more complex ways as well as letting fake entities appear more realistic (don't ask me how to do so without having legitimate players see them), it'll at some point impact system performance, without much potential to actually gain ground, in terms of clients not being able to track real vs. fake.
* Moving away from a more or less direct detection to posing traps for entity trackers is a different topic and has nothing to do with the current "hype".

## Conclusion
* Using fake entities will catch current simple clients for a while, but it should be possible to detect and bypass that in generic ways. It's not feasible to use this method on the medium/long run.
* Server side pattern detection will be similarly easy to bypass by adapting cheats, however there is a much higher chance to catch stuff after adjusting patterns to new cheats/clients than with using entities that can be ignored by cheats in generic ways.
