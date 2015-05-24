Config path: `checks.chat.text`  
Permission (bypass): `nocheatplus.checks.chat.text`  
Exemption: `CHAT_TEXT`  

This is a complex check which is designed to stop chat spamming by assigning a configured amount "weight" to every chat message. NoCheatPlus will prevent further chat activity of someone that exceeded that weight and punish him based on what is set in your actions.

| Option           | Description |
| :--------------- | :---------- |
| allowvlreset     |  |

## Frequency
This check is split in 2 frequency's to cover both fast and slow chat spamming.  

### Normal
Here you can configure the long-term variant which analyses the chat from **30** seconds ago.

| Option           | Description |
| :--------------- | :---------- |
| minimum          |  |
| factor           |  |
| weight           |  |
| level            |  |

### Shortterm
Here you can configure the short-term variant which analyses the chat from **5** seconds ago.

| Option           | Description |
| :--------------- | :---------- |
| minimum          |  |
| factor           |  |
| weight           |  |
| level            |  |

## Message
This section allows to alter message-specific weights.

| Option            | Description |
| :---------------- | :---------- |
| lettercount       |  |
| partition         |  |
| uppercase         |  |
| afterjoin         |  |
| nomoving          |  |
| repeatviolation   |  |
| repeatglobal      |  |
| repeatself        |  |
| words _lengthav_  |  |
| words _lengthmsg_ |  |
| words _noletter_  |  |

## Global

| Option              | Description |
| :------------------ | :---------- |
| weight              |  |
| words _active_      |  |
| prefixes _active_   |  |
| similarity _active_ |  |

## Player

| Option              | Description |
| :------------------ | :---------- |
| words _active_      |  |
| prefixes _active_   |  |
| similarity _active_ |  |

**Related**   
* [Active](Global#Active)
* [Actions](Global#Actions)
* [[Chat] Captcha](%5BChat%5D-Captcha)
* [Long-term and Short-term](Backgrounds#long-term-and-short-term)