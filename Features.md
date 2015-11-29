## Movement
* Prevents or limits flying
* Prevents speeding by sending too many moves
* Prevents speeding with vehicles by sending too many moves
* Enforces fall damage
* Prevents no-clipping

## Net (Require ProtocolLib)
* Prevents from spamming flying packets to nail other players down in their tracks or cause other unwanted side effects 
* Prevents from tracking down other players by abusing a weakness in the Minecraft weather
 
## Fight
* Enforces sane turning speeds
* Prevents hitting of multiple entities at the same time
* Prevents fake critical hits
* Forces to look at the entity before hitting
* Prevents fast health regeneration
* Prevents invulnerability
* Enforces arm swing on fight
* Prevents hits that have gone out of reach
* Prevents too many hits in a row

## Block breaking
* Forces to look at the block before breaking
* Prevents quicker block breaking
* Prevents from breaking multiple blocks at the same time
* Forces arm swing on block breaking
* Prevents breaking of blocks that are out of reach
* Forces to interact first before breaking the block

## Block interaction
* Forces to look at the block before interacting
* Prevents interaction with blocks that are out of sight
* Prevents interaction spam
* Prevents interaction if block technically not visible

## Block placing
* Prevents placing blocks against liquids and air
* Enforces cool-down for sign placement
* Forces to look at a block before placing
* Prevents placement of multiple blocks at the same time
* Prevents block placement if out of reach
* Forces arm swing on block placement
* Prevents projectile spamming

## Chat
* Prevents text spam
* Prevents command spam
* Implements captcha capabilities
* Prevents re-logging spam
* Prevents login spam

## Combined
* Prevents faking of "bedleave" packets
* Prevents enderpearl abuse (noclip)
* Prevents advanced fight cheats by combining multiple fight checks in one
* Removes invulnerability on login

## Inventory
* Prevents dropping of too many items at the same time
* Prevents cheated inventory management
* Prevents bow and arrow spam
* Enforces eating speeds
* Closes inventory in some cases to prevent dupes

## Other
* Forces commands like /op and /deop to be ran in the console only
* Can send MOTDs to control some client mods that support it (Reis minimap etc.)
* Prevents creating books with unlimited pages
