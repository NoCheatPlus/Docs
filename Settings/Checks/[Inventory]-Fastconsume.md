Config path: `checks.inventory.fastconsume`  
Permission (bypass): `nocheatplus.checks.inventory.fastconsume`  
Exemption: `INVENTORY_FASTCONSUME`  

Fastconsume replaces the former Instanteat check and extends it by forcing vanilla consume durations on potions, water bottles and more.

| Option              | Description |
| :------------------ | :---------- |
| duration            | Multiplier of how long it should take to consume a item. |
| whitelest           | True means that Fastconsume will only check the items you have  added in your list. False means that Fastconsume ignores all items you added in your list (option below). |
| items               | You can add items here that you want to whitelist/blacklist from the Fastconsume check. |

**Notes**
* NoCheatPlus will automatically fallback to "Instanteat" if your server does not support the consume event which fastconsume needs to work.
* Setting duration higher will require players more time to consume the item while setting it lower allows them to consume it quicker

**Related**  
* [Active](Global#Active)
* [Actions](Global#Actions)
* [[Inventory] Instanteat](%5BInventory%5D-Instanteat)