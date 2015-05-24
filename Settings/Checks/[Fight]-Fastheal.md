Config path: `checks.fight.fastheal`  
Permission (bypass): `nocheatplus.checks.fight.fastheal`  
Exemption: `FIGHT_FASTHEAL`  

This check prevents players from generating healthy faster then possible.

| Option              | Description |
| :------------------ | :---------- |
| interval            | Interval in ms (milliseconds) between regaining health (from saturation). |
| buffer              | Fastheal will count away from the buffer to fit your set interval if a player healed up faster then usual (lag). So here you set the value in ms (milliseconds) that Fastheal is allowed to buffer. |

**Notes**
* In Minecraft 1.6 and older a player could faster generate health by spamming movement packets, this was later on changed in MC 1.7.x and higher to generate health based on server ticks instead. However there seem to still be some cases left where players seem to still be able to generate health faster which is the reason why we didnt remove Fastheal from NC+.
* Fastheal has a buffer to prevent false positives by smoothing out lag spikes
* You want to only adjust the interval if your server heals your players faster/slower for some reason (mods?)

**Related**  
* [Active](Global#Active)
* [Actions](Global#Actions)