This page describes the fundamentals of what NoCheatPlus is based upon.

# Levels of Protection and Detection
The fundamental concept of NoCheatPlus is to cover the most important grounds for survival game play with _deterministic protection_ in the first place. This means the protection is meant to still be there after cheat clients have updated, and it can only by bypassed if there are bugs. Naturally not all possible cheats are covered or are even possible to cover, and cheat clients can adapt to the limits in some cases, but they can't _break_ the limits.

The next layer consists of _heuristics and educated guessing_, which may be more prone to allow actual bypasses, but which are likely to hold for a while, due to the conception aiming at fundamental mechanics of legitimate game play rather than detecting specific behavior of cheating, the latter of which could change with a cheat client update.

The thing we do least is _detecting specific cheats or patterns of cheating_, which usually allows a cheat client to completely bypass the checks with the next client update, in which case we would end up with _hourly updates_ on both sides. Such an approach would allow for easier banning, however despite the _detection_ for a range of known cheats and cheat clients, it does not provide any actual long-term _protection_, which is why we don't rely on such methods in the first place.

Main reasons for taking the approach 'protection before detection' are:
* The level of protection the vanilla server provides by default is not very high.
* Manpower - this is the 'free' plugin, and we need to provide something usable, without burning all our brain with cat and mice play. Thus we focus on rather lasting things in the first place.

# False Positives
A large amount of time is spent with testing and balancing, in order to not cause or at least to reduce false positives. For game play, false positives can be show stoppers. It's worth nothing to detect a cheat, if we cause game play breaking false positives - supporting a wide range of server types means not underestimating this aspect.

To be able to confine better what cheating can do, we also must keep false positives at bay by design, otherwise we too often end up with reducing the sensitivity of a checking method, resulting in both less protection. Our primary approach is to create more precise envelopes for legitimate client behavior based on experience and diligence, thus we need to account for the physics of things, just to avoid the word _mechanics_ for a split second. Naturally with multi-player games there is latency, networking congestion and just _lag_ of other type on client- and/or server-side. In order to reduce or fully remove false positives, we will need infrastructure to be able to (rather) deterministically determine what may be or may have been the case at the time of the client side taking action. It can't be achieved by allowing a wider range for hitting, for a simple example.

# Abstraction and Infrastructure
Many servers stay on the previous version of Minecraft, when a Minecraft update happens. Such can cover longer phases, thinking of 1.7.x ... 1.8.x ... 1.9. Thus we support multiple versions of Minecraft by default. It's harder to remove compatibility than to keep going, most of the time, and cheat clients tend to be written for the most used versions of Minecraft.

Infrastructure is needed for things like:
* Piston compatibility (future: pushed a block far, moving through blocks, on-ground?). Also concerns other block changes like doors, block breaking and placing by others, blocks changing with redstone or gravity.
* Latency and precision with fight checks (part future).
* Judge player moving (past moves with details about the environment).
* Efficiency with testing for map/block properties over and over.
* Keeping code changes minimal for a new version of Minecraft, because checks can rely on the infrastructure to remain mostly unchanged.

Of course infrastructure is expensive, as it does not catch cheaters directly, and it's either lengthy or even difficult to create, or at least it needs experimentation. Experience tells that so far, the approach has paid off manifold.

# Conclusion
Ideally multiple developers should share time to create a future open-source thing, instead of wasting time with detecting individual instances of cheat implementations (...). We've at least shown what could have been done much faster with people sharing resources.
