Config path: `checks.chat.captcha`  
Permission (bypass): `nocheatplus.checks.chat.captcha`  
Exemption: `CHAT_CAPTCHA`  
Depends on: `[Chat] Commands` or `[Chat] Text`

The captcha feature can be used together with our text or commands spam check to ask players that fail one/both of those a randomly generated captcha, which needs to be answered in order to continue.

| Option           | Description |
| :--------------- | :---------- |
| characters       | Which chars (numbers, letters and symbols) should be used to generate a captcha? |
| length           | Set amount of characters the captcha should have. |
| question         | How should the question be worded? Use & to create formattings. The text [captcha] will be replaced with the actual captcha. |
| success          | Set the message which will be shown to the player if he/she answers with the right captcha. |
| tries            | How many attempts will a player have to give the correct answer. A failed attempt will display the question again. Be generous here, as players may not be fast enough to read the question the first few times or be otherwise distracted. |

**Related**  
* [Active](Global#Active)
* [Actions](Global#Actions)
* [[Chat] Text](%5BChat%5D-Text)
* [[Chat] Commands](%5BChat%5D-Commands)
* [Formatting codes](http://minecraft.gamepedia.com/Formatting_codes)