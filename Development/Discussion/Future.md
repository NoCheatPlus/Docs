# Future

This page is meant to give some insight and base for discussion of what NCP will look like in future.

Version:
* Initial draft, likely leaving out a couple of points.
* Some points contain random explanations, these and/or the placement of these are subject to discussion too, could be moved to other sections.
* Most are not PR-points, but more or less inevitable directions to at least check out.
* Feel free to discuss any part of it all (code, modeling, design, project structure, support structure, ...).

## Current State

On the current state of the NCP code base, what is real and what not.

Over time there have been experimental additions and tests about data structures and infrastructure, some of which have been very successful in general, some of which may not have been far reaching enough to be kept in a future version of NCP.

NCP is a somewhat working system, so the focus of changes has not always been to lay out a perfect future design, instead recently the focus rather had been to check if/how false positives can be kept at bay and to patch up places towards the point of recode (!), at least for some places like moving checks. So if you think some places look ugly, you're probably right.

Current focus of development is to keep changes 'cheap' and to rather simplify/unify things based on experience, not changing too much at a time to avoid costly debugging - this means shifting the focus towards future design.

## Design Aims

What are the main aims of changing anything at all?

The absolutely most important point is, that there is need for a decent open source plugin of this kind, otherwise i'd call it a day with Minecraft, simply, because i need this to run a server at all. Which alternatives are there?
* Other projects? Name one, i'm interested.
* Why not drop it or wait until someone does something simplified once again? Essence of past years experience is, that more complex frameworks are needed to keep things at bay. That involves things like past-move tracking for players, both for false positives and detection with moving checks, but also to deal with latency for interacting with entities like with fighting, or things like past block change tracking to be able to support pistons (unfortunately there is multiple areas involved: sudden fast moving, on-ground judgement, passing through blocks). In order to not become insane and also to deliver performance, block shapes and similar need an abstraction framework, to stay independent of changes between Minecraft versions and also to allow smart caching to improve performance. Some of these have already been prototyped or are even in use by now, but there still is some ground to cover, also considering questions like which data to share for similar contexts (moving and fighting need some kind of past move data), if/where to unify data. With unifying data you need to account for differing checks (e.g. move vs. fight) having different needs for things or different views on things, concerning resetting past move validity (!). So my conclusion about Minecraft is, that the idea to have a small code base simplified approach is nothing you can have for open source anymore, you will need to have infrastructure, and to keep developers interested, prototyping and handling checks needs to be convenient, which needs even more infrastructure. Also consider supporting a range of vanilla features, some of which aren't even accessible via the Bukkit API, and some of which have to be treated with latency in mind, thinking of attributes, potions, sprinting. Specifically with attributes you have the inaccessibility via API coupled with inconsistent data state, concerning sprinting and latency in general. So i won't set my money on a simple-by-default approach, neither will i go with a closed source black box that detects specific client versions.
* What if the registries + infrastructure approach fails? I'll not wait for the community to patch up things next year, neither will i wait and see if 'the paid resources market' can 'heal' the situation :p. Paid black boxes are not an option, doing without the 'classic' envelope checks is not an option.
* It could be an option to have someone/team combine approaches, by having an open source plugin cover the worst with classic checks, open to contribution, and to have a paid subscription-based service for downloading latest/best patterns/data for detecting specific instances of cheat implementations and/or clients. The pattern/machine code would be open source too, the entire plugin needs to be open source. Dynamic code generation can only involve accessing nms properties or constructing optimized arithmetics, but not loading code for the paid feature (i.e. a full security review is possible given the public plugin source). This also implies that anyone else could in theory create a compatible data service, so this is not something you miracle up lightly, and you do need a reliable team to back this kind of thing up. I am also not too convinced that such a plugin would be so much simpler to code, thinking of supporting more than one server/gameplay type.

From my side the biggest points are:
* Dramatically increasing the surface towards contribution by others.
 * Get more developers on the boat.
 * Make the code so inviting that any other developers may feel to prototype their idea, achieve so quickly and efficiently, and may feel inclined to contribute on occasion.
 * Allow non-developers to contribute in even more significant ways.
  * Make new parameters accessible via configuration, so testers can help adjusting them, without need for coding experience. This demands splitting the configuration into multiple files, in order to prevent peaceful users from detonating their server via model/magic config editing. Possibly other changes are necessary as well.
  * Increase the logging capabilities, making use of infrastructure such as past move tracking. A good example is to allow recording incidents (in a smart way :p), so a server owner could somehow review an issue and use a recorded bit of a past move trace to potentially deal with false positives as well as cheating. This could involved logging stored sequences as reports, but it could also involve adding configurable workarounds or cheat detection based on the past-move data. Depending on how smart things are done, this could be used for training of machine learning components, as well as catching stuff directly. The workaround/counter infrastructure will help allowing to confine things to 'once per in-air phase' or potentially other (allow workaround twice per minute, etc. ...).
* More if not vastly mod-independent design. One main reason for doing so is the implicitly following abstraction enabling us more easily to record user behavior to the benefit of all sorts of areas (replay, testing, compare similar instances with adaptive cheat detection, auto generate cheat detection :p). Another benefit is of course, that we become more independent of the Minecraft version (see below: Minecraft version agnostic design).
* Minecraft version agnostic design.
 * Similar to mod-independence, abstraction and a data source framework allows to provide all sorts of access/data specific to server versions or other specific dependencies, e.g. ProtocolLib. The cost of supporting multiple Minecraft versions is much reduced, as we can just have new providers - possibly more fine grained, so we only need to override what's needed. 
* Dynamic check and listener registration.
 * Allow overriding checks and have their listeners be auto-removed.
 * In case of Spigot, this demands having our own listener registry framework.
 * Allow an extra priority for listeners, to guarantee sorting order. This allows a reliable sequence of processing, also having compatibility extensions in mind. Ease of registry included, as you don't need to care for the exact time of addition of a listener.
 * Allow unregister checks at runtime, checks can be replaced by simplified/other checks, even by other plugins. Auto registry features help simplify such processes towards 'simple'.
* Flexible registries and supported paradigms, one-class check registration.
 * It should be possible to set up a new prototype/check with one class, even from an external plugin. Default config (including all complexity with multiple world and split config file support) as well as dynamic check type registration or re-use/overriding should be possible.
 * Dependency handling and auto registration: A registration context thing allows to auto register and unregister (!) your check, depending on availability of dependencies, such as other plugins, other checks, data providers.
 * Support all sorts of conditions for registering/unregistering components of any kind.
* Centralized data and configuration storage.
 * Enable per-player data + configuration same way as per-world and global.
 * A per-player data broker will allow to store any kind of data, so adding your check and specific data classes will be easy.
 * Reliable per-player data and settings in a central place (exemptions, check data, which checks to run...)
* More flexible concepts for violation level handling.
 * Generic counter framework, allowing to combine all sorts of inputs (also include frequency, current level, just added level, arithmetics and other as triggers), also allow to create new meta-checks.
* More flexibility for configuration.
 * Make stuff switchable with global switches (severity).
 * Attempt to actually implement methods of sensitivity and allow to distinguish between 'hard limit' vs 'sensitivity' (e.g. 'can't possibly decrease speed like that' vs. 'a little too fast in average').
* New types of checks, new methods, new check design.
 * Specific check design is not discussed in this section, of course much is possible there.

Some of the aims can be postponed a lot, e.g. abstraction can be done bit by bit for some contexts, as it'll be possible to add legacy data sources and use the registry with its dependency handling to add in the checks if necessary.

An example for flexible registration could be moving checks that use a specialized abstraction for accessing properties of blocks or the environment in general - the registry could prefer specialized providers when available, but it could also add-in adapters that create the specialized provider from a potentially less optimized general provider, if no specialized/optimized thing is available. Overriding dynamic providers with read-from-config providers would be possible, as well as overriding something for your custom build of Minecraft.

## Recode versus Transformation

Depending on manpower, there are various ways to continue, some of which are between recoding from scratch and more or less slowly transforming the current code base to a new thing.

Since this is still/always an open point to discuss, i want to mention some edges that we detected throughout the past.

Benefit of a recoding (part or whole).
* New design doesn't need to account for past debt.
* Less distraction by past code/approaches.

Problems with recoding (part or whole).
* Much longer way to have an overall working thing.
* Longer way towards testing the concepts at all.

Benefit of transformation:
* New approaches can be tested/prototyped faster, if they can be added in to existing frameworks.
* New implementations will reach a large user base, even if just within development builds.

Problems of transformation:
* Actual target implementation may be impossible due to not yet existing framework parts, leading to a higher cost of implementation in total for adapting the implementation to the old framework.
* Some (typically infrastructure-related) additions are impossible to be used by old checks, for the complexity of changes.
* Some paradigms can't be added in general (e.g. side effect free check design), because old checks need to be transformed to use those, potentially expensive.

Synthesis:
* Some concepts can and should probably be tested early, with an as big as possible user base for fastest results.
* Some concepts can be implemented and added in to the existing plugin, even if old checks don't use those.
* Likely going as far as reasonable with transformation first, is the best thing to do.
 * Sketch out as many new infrastructure and checking methods, where we can keep the cost for a switch to a future design as low as possible.
 * Where we need experiments, things should be tested early.
 * Postpone incompatible changes until we can make an as fast as possible transition.
 * Rather wrap complex existing checks that can't be transformed internally as new-style standalone checks, using their own private data. Avoid expensive recode to a new system. This may be overestimating the cost, as even the complex moving checks are already using internal objects that will allow abstracting things pretty quickly - i just won't rush forward with another potentially expensive change, unless there is a clear aim to get to with.

Examples for synthesis:
* A new check design might be mod-independent for most, however in order to progress quickly, a generic data source framework still allows us to add data sources for Bukkit/Spigot legacy checks that then run outside the intended target design with minimum code changes (!). Check interaction can suffer here, but the point is to cover ground quickly.

# Schedule

Independently from what would happen with a 'new thing', or say a team forming, i'll give some examples what is likely to happen, provided things continue anyway. Also compare to the Development/Roadmap.md document, some points may be contained in Development/Discussion/Design.md document.

To give an outlook on what will happen anyway:
* Piston compatibility. No matter what, this will be attempted to bring in now, as design is comparably expensive and much of the already present infrastructure is needed. A large user base is needed for testing as well.
* At least implement fight check related penalties (already begun, but postponed due to vehicles / 1.9.4 / whatever). These allow dealing penalties as actions based on probability checks and with alternatives (FCFS or apply several, think of reducing attackers ndt, damage reduction, cancel with probability, other), which enables us but also config-savvy users to start penalizing "earlier", without hard cancelling from start.
* Improve fight checks, making use of all available infrastructure (basic run, but may change a lot): penalty frame work, more detailed past move tracking, keep all past moves in the location trace without merging (TBD). New check design for estimating the difficulty of action.
* Better data expiration handling (more fine grained, keep the most important always, centralized).
* Some less complex scheduled changes, interact ray tracing, other.
* Somehow patching the worst that appears to be there.

Examples for things that might make it into old-style checks (likely but slightly uncertain):
* Splitting the configuration (quite likely to happen). Undecided how exactly, if to use sub folders for worlds/contexts. Likely a global root config, language, and splitting typical check config vs. model/magic somehow. Likely allow specifying worlds to apply it for within a configuration, while then the naming is more arbitrary.
* Horizontal velocity overhaul (aim: as precise as vertical, difficulty: we don't always have the correct values, so some values are exact, some aren't + latency etc...).
* More side effect free check design (here: player moving). This could be rewarding to already test with player moving checks, at least aspect-wise. Current consideration is to not alter the (not even permanent anymore) MoveData (or even MovingData) when a workaround is used, but to pre-store  applicable workarounds and their effect, in order to allow better post-failure processing and to allow decoupling horizontal vs. vertical move handling, which both need some common workaround checks.
* Fly checks for all types of vehicles, including those that can jump (more generic design then).
* Central data + configuration handling (PlayerData -> specific registered types).
* Dynamic check types. Potentially a medium-expensive change, but might be inevitable, positive effects for some data handling areas.
* Counter (includes violation levels) framework. Even the simplest form allows violation levels to be accessed in generic ways, and also enables more action-specific enhancements (relate to number of violations, relate to numeric level, relate to frequency of either).
* Overhaul of the entire actions framework. Coming with counters likely, relates to the already begun penalty-framework, may involve configuration changes, which then again might demand changes in the entire configuration setup (more flat action layout, hide default actions in another file, more complex, thus not 100% likely).
* Move more stuff from static to non-static (keeping NCPStaticAPIProvider, possibly rename to more simple :p).
* New (still classic) methods of tracking frequency / phases of intensity. Involves data structures (e.g. a list of phases of similar frequency/intensity). May experiment/use for judging differing types of actions vs. each other, more packets checks, other.
* Offline data. Might keep set-backs and some other edge/context to see if data should be loaded from disk or not.

Here examples on what i might not do with old-style checks:
* Latency aware parameters (generic implementation) for moving checks. Likely i'll keep what about works, and not attempt these, though this is a bigger future point/thing.
* Abstracting away the attributes (API and consistency are rather not-existent currently - an abstraction could enable all sorts of ways of providing latency-aware speed information for the player, similar to the above point).
* Add detection of specific clients other than providing a generic counter/input framework (i.e. maintaining the testing and updating of db/machine/pattern myself + for free -> nope). If others provide patterns (and test those), this could be considered. It's also thinkable to add "branding", like pattern of spigotmc.user123, so people can activate/deactivate by provider branding (and possibly consider buying the non-free patterns from them :p). It's not a lack of potential, it's just not feasible for me just now.
