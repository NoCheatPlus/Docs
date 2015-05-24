Config path: `checks.chat.warning`  
Depends on: `[Chat] Text` or `[Chat] Commands`

Allows you to warn the player of the chat.text and chat.commands weight levels, possibly before a violation is triggered.

| Option         | Description |
| :------------- | :---------- |
| level          | Percentage of level at which to warn. |
| message        | This message will be sent to all of the players that fail a chat check. |
| timeout        | Time in seconds before warning again. |

**Notes**
* Currently warning does not necessarily happen before violations are being triggered.
* Color codes are supported in message config
* If for example your CHAT_TEXT_SHORTTERM check has level set to 160 you calculate: (160 / 100) * level you set here in warning. Result= The level at which warning will trigger for CHAT_TEXT_SHORTTERM

**Related**
* [Active](Global#Active)
* [[Chat] Text](%5BChat%5D-Text)
* [[Chat] Commands](%5BChat%5D-Commands)