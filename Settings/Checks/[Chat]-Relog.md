Config path: `checks.chat.relog`  
Permission (bypass): `nocheatplus.checks.chat.relog`  
Exemption: `CHAT_RELOG`  

Relog prevents players from re-logging too fast.  

| Setting                | Description |
| :--------------------- | :---------- |
| timeout                | Time in ms (milliseconds) which a player has to wait before re-logging again. |
| warning _message_      | Set the warning message that will get sent to all players that tried to relog too fast. |
| warning _number_       | Amount of warnings that need to occur before kicking a player for "too fast re-logging". This resets after "warning timeout" executed. |
| warning _timeout_      | Time in milliseconds after which the number of warnings sent resets. |
| kickmessage            | Message to display when a player gets kicked by relog check. |

**Notes**
* Warning message supports [color codes](http://minecraft.gamepedia.com/Formatting_codes)

**Related**
* [Active](General#Active)
* [Actions](General#Actions)