This page explains the "behind the scene" tricks of NoCheatPlus, how it works and more.

### Asynchronous

`When you execute something synchronously, you wait for it to finish before moving on to another task. When you execute something asynchronously, you can move on to another task before it finishes....`  
[Adam Robinson (Stackoverflow)](http://stackoverflow.com/questions/748175/asynchronous-vs-synchronous-execution-what-does-it-really-mean?answertab=active#tab-top)

NoCheatPlus does a couple of things asynchronously to improve performance on your server.  

### Long-term and Short-term
Some checks like BLOCKBREAK_FREQUENCY implement another checking interval (shortterm) to catch and prevent very quick cheating more smoothly then the normal (longterm) check interval.

Especially checks like FIGHT_SPEED profit from this since damage to a player/creature is hard to undo. So a cheater would get instantly stopped by the shortterm interval if he/she tried to hit a creature/player 30 times in 10 server ticks.

### Ray tracing

### Violations
To count cheat attempts we use "VL" which stands for violation level in NoCheatPlus and its used 
by Actions and Strings to punish players based on their violation level.

**Notes**  
* Every check has its own violation levels and generates them in a different way based on how the check counts (SurvivalFly will reach much higher VLs compared to BedLeave)
* Backgrounds
* By default the violation will be kept till you restart your server (even on log out)
* Violation levels that have been logged are different compared to those shown in the info or history command because the command ones only show the VLs that have been added
* Many cheat clients are adapted to cause as small as possible levels, thus distinction of false positives and cheating becomes harder and harder.
* Make use of **/ncp info <PLAYER>** to have a rough idea how many different checks the player triggers (also compare output for differing times).