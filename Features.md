## Compatibility
NoCheatPlus features a range of compatibility features.
* Compatibility with multiple versions of Minecraft. You can rely on the latest version of NoCheatPlus still running on a range of past versions of Minecraft.
* Configuration allows working around issues with specific blocks (custom mods, early adopter).
* A range of API features to allow developers to make their plugins compatible (exemption API, exemption by meta data, hooks for violation processing, other).
* Default exemption for NCPs, such as with Citizens.
* Vanilla features. It may not seem worth mentioning, but we can't support all features to arbitrary depths. Still you will find that NoCheatPlus provides a balance between supporting vanilla features, extensions like higher level potion effects and attributes (vanilla too, but usually not encountered without command blocks or adventure maps), and finally protection from abusing those features vs. false positives. Our aim is to support all vanilla features, of course, it's a larger task than you might think.

## Movement
* Prevents flying.
* Limits speeding (packets and apparent speed).
* Prevents speeding by sending too many packets.
* Enforces fall damage.
* Prevents no-clipping.
* Prevent vehicle flying (1.9+)
* Limit vehicle speeding (packets and extreme distances).

## Net (Require ProtocolLib)
* Attacking frequency monitoring (not possible otherwise).
* Prevents from spamming flying packets to nail other players down in their tracks or cause other unwanted side effects
* Prevents from tracking down other players by abusing a weakness in the Minecraft weather
* (Further tweaks against false positives.)
 
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
* Prevents a range of text spamming variants.
* Implements captcha capabilities.
* Prevents re-logging spam.
* Prevents login spam.

## Commands
* Prevents command spam.
* Allows to treat certain commands as chat.
* Confine commands like op and deop to be used from the console only.

## Combined
* Prevents faking of "bedleave" packets.
* Prevents enderpearl abuse (noclip).
* Limits advanced fight cheats by combining multiple fight checks in one.
* Removes fall damage invulnerability on login selectively (configurable damage types!).

## Inventory
* Prevents dropping of too many items within too short time.
* Prevents some forms of inventory management.
* Prevents bow and arrow spam.
* Enforces eating speeds.
* Closes inventory in some cases to prevent ever-reappearing duplication bugs.

## Other
* Can send MOTDs to control some client mods that support it (Reis minimap etc.).
* Prevents creating books with unlimited pages.
