Config path: `checks.chat.logins`  
Permission (bypass): `nocheatplus.checks.chat.logins`  
Exemption: `CHAT_LOGINS`  

This check limits the amount of players that can join in a short time.

| Option             | Description |
| :----------------- | :---------- |
| startupdelay       | Set delay in seconds till NoCheatPlus enables this check after a server start. |
| perworldcount      | If set to true, the counting will be performed for each world individually and not server-wide. |
| seconds            | Duration in seconds before NoCheatPlus purges the login data and starts counting all over again. |
| limit              | Number of logins that may happen within the specified time (seconds). |
| kickmessage        | This message will be shown to those players that get kicked because too many other players logged in at the same time. |


**Related**   
* [Active](Global#Active)
* [Actions](Global#Actions)