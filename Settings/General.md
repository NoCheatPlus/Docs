This page lists all the config options that apply to the multiple existing features.  

# Active
Just a simple on/off switch for most features.  
**True**: Enables that feature  
**False**: Disables that feature 
 
**Notes**
* Remember that NoCheatPlus will still load up the check on start-up even if its set to false.  
* Disabling a dependency form another check will turn it into a ghost (Wont do anything, like its disabled)  

# Actions
"Actions" is kind off the task scheduler of NoCheatPlus, here you define which actions NC+ should take at a defined violation level.  

## Overview and Customize 
| Action        | Description  |
| :------------- | :------------|
| **cancel**    | The effects of the action "cancel" depend on the check that it is used for. Usually it means to prevent something from happening, e.g. stop an attack or prevent sending of a chat message. `cancel` |
| **log**       | Create and show/log a message. Log messages can be customized in how often, when and where they are registered/shown. `log:string:delay:repeat:target` <br> `log` Is simply used to let NoCheatPlus know that this is a log action. </br> <br> `string` Here you define the message that will be logged over a string (check strings reference). </br> <br> `delay` A number declaring how many times that action initially has to be executed before it really leads to logging a message. Use this for situations where it's common to have false positives in checks and you only want the log message to be shown if a player fails the check multiple times within a minute. </br> <br> `repeat` A number declaring how many seconds have to pass after a message has been logged before it can be logged again for that player (cooldown). This is needed to prevent "log-spam". Usually a value of 5 seconds is acceptable, for rare events you can use lower values. It is recommended to at least use the value 1 (one second) here. </br> <br> Example: `log:bdirection:0:5:if` </br>
| **cmd**       | Execute a command of Bukkit or another plugin as if it were typed into the server console by an admin. Like logging, these can be customized. `cmd:string:delay:repeat` <br> `cmd` Is simply used to let NoCheatPlus know it is a command action. </br> <br> `string` Here you define which string (read strings reference) should be taken to execute as command. </br> <br> `delay` A number declaring how many times that action initially has to be executed before it really leads to logging a message. Use this for situations where it's common to have false positives in checks and you only want the log message to be shown if a player fails the check multiple times within a minute. </br> <br> `repeat` A number declaring how many seconds have to pass after a message has been logged before it can be logged again for that player (cooldown). This is needed to prevent "log-spam". Usually a value of 5 seconds is acceptable, for rare events you can use lower values. It is recommended to at least use the value 1 (one second) here. </br>
| **vl>X**      | Is meant to symbolize "violation level at least X". Used to define actions that will be executed only if players reached a certain violation level. Failing a check usually increases their "vl", not failing checks reduces it over time. Violation levels mean different things for different checks, e.g. they may describe moved distance beyond the limit, number of attacks above the attack limit, sent messages beyond the spam limit. <br> The "vl>x" isn't really an action. It limits all actions that are written afterwards to be only executed if the players’ violation level has reached at least the given value. This allows defining layers of actions and handling repeated or severe failing of checks different. For example the spam check will only kick players if they reach a certain violation level (vl). </br> |

**Template**  
![Action Explenation](Resources/ActionExplenation.gif)  

**Levels**  
![Action Levels](Resources/ActionLevels.gif)  
Level 1: Will be executed if the violation is under 1000  
Level 2: Will be executed if the violation is in range of 1000-1299  
Level 3: Will be executed if the violation is 1300 and higher  

Once a violation level reaches a **vl>X** limit all actions before that limit will become obsolete and wont be executed till the violation level goes down again. Now NoCheatPlus will execute the actions which are in the current level. Remember that executed commands wont be rolled back, so if you banned someone on level 2 he/she wont get unbanned on level 3 unless you specified it in your actions.

**Notes**  
* For some checks immediate kicking or teleporting of players is not recommended, because it can conflict with the set-back logic or further event-processing, such as with the flying checks - for those we recommend to use the command prefix "ncp delay ", in order to run the actions outside of the event processing.
* Always make sure to **cancel** first before you do something else (for example kick) to avoid exploits with checks not canceling properly
* The ":delay:repeat" part can be omitted from the "log" and "cmd" actions

**Related**  
* [Strings](Strings)
* [Violations](Backgrounds#violations)