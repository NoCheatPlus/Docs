Config path: `checks.chat.commands`  
Permission (bypass): `nocheatplus.checks.chat.commands`  
Exemption: `CHAT_COMMANDS`  

This check aim to prevent command spamming (player chat only).

| Setting           | Description |
| :---------------- | :---------- |
| exclusions        | A list of case sensitive commands to exclude from the commands check. Commands to match complete words, you cant add "/test" to allow "test123", whereas it is possible to use entries like "/region info" to exclude just that sub command. |
| handleaschat      | A list of commands that should be handled by the text check instead. Typically makes sense for commands like "/me". Matching is the same principle as with exclusions. |
| level             | Set spam level at which the commands check will throw 1 violation. |
| shortterm _ticks_ | Number of server ticks to count commands for shortterm checking. |
| shortterm _level_ | Level for which to generate an exception. |

**Related**
* [Active](Global#Active)
* [Actions](Global#Actions)
* [[Chat] Text](%5BChat%5D-Text)
* [[Chat] Captcha](%5BChat%5D-Captcha)
* [Long-term and Short-term](Backgrounds#long-term-and-short-term)