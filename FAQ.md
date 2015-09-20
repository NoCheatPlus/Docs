**Table of Contents**
* [Why is aimbot/killaura not detected by NoCheatPlus?](FAQ#why-is-aimbot/killaura-not-detected-by-nocheatplus)
* [Why does NoCheatPlus not detect NoKnockback?](FAQ#why-does-nocheatplus-not-detect-nokncokback)
* [Why use NoCheatPlus instead of plugin X?](FAQ#why-use-nocheatplus-instead-of-plugin-x)
* [NoCheatPlus does not block any hacks on my server, I can login with any hack client and grief as much as I want without getting blocked?](FAQ#nocheatplus-does-not-block-any-hacks-on-my-server-i-can-login-with-any-hack-client-and-grief-as-much-as-i-want-without-getting-blocked)
* [I gave my friend permissions for a mod but he stills get blocked by NoCheatPlus?](FAQ#i-gave-my-friend-permissions-for-a-mod-but-he-stills-get-blocked-by-nocheatplus)
* [Will NoCheatPlus support plugins like mcMMO and Citizens out of the box?](FAQ#will-nocheatplus-support-plugins-like-mcmmo-and-citizens-out-of-the-box)
* [Why isn't cncp (CompatNoCheatPlus) already integrated in NoCheatPlus?](FAQ#why-isnt-cncp-compatnocheatplus-already-integrated-in-nocheatplus)
* [Can i use NoCheatPlus with another anti-hack plugin?](FAQ#why-do-you-have-commands-like-ncp-ban-ncp-kick-and-other)
* [Why do you have commands like /ncp ban, /ncp kick and other?](FAQ#why-use-nocheatplus-instead-of-plugin-x)
* [Is banning based on check alerts encouraged?](FAQ#is-banning-based-on-check-alerts-encouraged)
* [Where is the "donate" button?](FAQ#where-is-the-donate-button)

### Why is aimbot/killaura not detected by NoCheatPlus?
NoCheatPlus covers a large potion of pvp (player versus player) and pve (player vs enviorment) cheats (see [Features](Features#fight)) but there are invisible problems now.  
**The client sided hacks** Since NoCheatPlus can only use the ressources which are controled and aviable on the server we are in that case limited to what we can detect. Aimbot for example is besically a hack that just looks at another player/entity and hits it, so there is no way telling if that action was done by a real player with his mouse or by an aimbot. Most up to date aimbots are actually really smart and do random "errors" or even a view motion (do not turn around too quickly) to simulate a real computer mouse.  
**The big mouth but nothing behind** Some hack clients have a GUI which over advertise the clients hacks by doing big flashy red large buttons and a description such as "*This OP hack bypasses NC+ and lets you win every game!*" . However what such hack clients mostly do is just look at the player and hit him with a reasonable hit speed that just stays under the radar of NC+ (If we would increase that limit there would be more false positives).  
**The weakpoints of NC+** Currently we can not properly detect fight.speed because our old method broke with the Minecraft 1.8 release, we are working on a new solution at the moment.

### Why does NoCheatPlus not detect NoKnockback?
Currently we have not found a good solution to track it down without using up a lot of ressources and create a lot of false positives. One of the key issue to why this has not been fixed yet is the fact that velocity is done client-side, so the server doesnt not really have much control over it.

### Why use NoCheatPlus instead of plugin X?
It is up to you! NoCheatPlus puts emphasis on configurability allowing you to choose when to kick, ban, log, do anything at all, also allowing to adjust a lot of parameters to tweak checks for your needs. Other plugins may put emphasis on simplicity of configuration. All plugins strive to work fine "out of the box" without need to adapt much. Of course every plugin might have strengths and weaknesses on different fields - we suggest you match your needs against the [features](Features) of the plugins, and ask if in doubt.

### NoCheatPlus does not block any hacks on my server, I can login with any hack client and grief as much as I want without getting blocked?
You probably have OP or permissions (administrator or owner rank) on your server which let you bypass all the NoCheatPlus checks. So if you want to test then deop yourself and set your rank to default. Also make sure your Minecraft version matches the version NoCheatPlus has been compiled for, it can be seen on the download pages of BukkitDev or simply using /version NoCheatPlus or /nocheatplus version

### I gave my friend permissions for a mod but he stills get blocked by NoCheatPlus?
After giving permissions to a player, he/she has to relog to activate there mods they got permissions for. Be warned: `nocheatplus.mods.zombe.fly` for example only gives the permission to enable zombes fly mod, you will also need the `nocheatplus.checks.moving.survivalfly` permission to make it work right.

### Will NoCheatPlus support plugins like mcMMO and Citizens out of the box?
NoCheatPlus does not have any special plugin dependencies built in, because they delay the update process of our plugin. Instead we provide you with a compatibility bridge called [CompatNoCheatPlus].  
CompatNoCheatPlus simply connects NoCheatPlus (reason why it needs to be installed alongside CNCP also) with other plugins such as [mcMMO], [Citizens] and others using the powerful [NoCheatPlus API](API) to make them compatible together.  
If you would like to suggest or implement another plugin compatibility in CompatNoCheatPlus then contact @asofold for additional support.

### Why isn't cncp (CompatNoCheatPlus) already integrated in NoCheatPlus?
Because it would slow down the development of NoCheatPlus, we would always have to keep up with the other plugins if those get changed, also changes to NoCheatPlus might break compatibility with other plugins, so we would have to fix those too or remove the broken hooks. Also the testing for those components takes a lot of time and can't really be done by us. We might at some point build in a couple of generic things that will help with _some_ compatibility issues without endangering us of getting stuck with compatibility issues.

### Can i use NoCheatPlus with another anti-hack plugin?
Two plugins usually are not better than one. Just activate the few checks of the other plugin that you assume to be useful, disable the rest. Best bet is to to deactivate either plugins fly checks, or all moving-related checks right away, because those will likely conflict. The typical problems are that checks or the the whole plugins... a) become less effective, because one plugin won't even register actions that a player did, due to the other plugin having cancelled the action already, which can happen to both plugins, due to differing limits... b) that the same kind of checks conflict in taking back players actions, leading to unpleasant effects, such as allowing flying with multiple fly checks being activated (also with the vanilla fly check!).

### Why do you have commands like /ncp ban, /ncp kick and other?
Those are auxiliary commands used for NoCheatPlus actions, you can execute them by hand as well.

### Is banning based on check alerts encouraged?
We don't encourage banning in general, because checks can have false positives and nowadays cheat clients adapt pretty well to the boundaries set by NoCheatPlus, so the "good ones" won't even create many violations. It does depend on the individual check, how it is affected by latency or lag or randomness, though. With the right choices, temp-banning could make sense for combinations of checks+alert-levels, if they are not too much influenced by random events or lag or latency.

### Where is the "donate" button?
It has been removed for the time being. We might re-add it once we are in need of donations.

**Related**  
* [Known Issues](Known-Issues).

[CompatNoCheatPlus]:http://dev.bukkit.org/bukkit-plugins/compatnocheatplus-cncp/
[mcMMO]:http://dev.bukkit.org/bukkit-plugins/mcmmo/
[Citizens]:http://dev.bukkit.org/bukkit-plugins/citizens/
