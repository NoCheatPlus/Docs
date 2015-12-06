Config path: `checks.combined.invulnerable`  
Permission (bypass): `nocheatplus.checks.combined.invulnerable`  
Exemption: `COMBINED_INVULNERABLE`  

Selectively alter or remove the initial invulnerability after login.

| Option                  | Description |
| :---------------------- | :---------- |
| triggers _always_       | Always apply the alterations. |
| triggers _falldistance_ | Trigger with the fall distance being greater than 0. Reduces the impact of this check, because most of the time players are not affected at all. |
| initialticks _join_   | Allows to override the amount of invulnerable ticks, whatever Minecraft is using. Default is -1 and means not altering. |
| ignore                  | Damage types for which the invulnerable ticks are to be ignored. By default FALL is set, to prevent abusing the login invulnerability to avoid fall damage. |
| modifiers | Define individual modifiers per damage type (the preset is defined with 'all'). The player will stay invulnerable for this amount of ticks longer/shorter for the specified damage type, allowing for negative values as well. |

**Related**
* [Active](General#Active)
* [Actions](General#Actions)