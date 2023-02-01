> ⚠️ **Warning:** This page is still under construction!
# Altars

## Overview
Altars are the core of a `Cult` as they are the only way to create a cult and only way to perform certain rituals such as `Sacrifices`. Altars are meant to be kept safe since destruction of the `Altar` triggers a configurable timer that will dissolve the `Cult` if the `Altar` is not rebuilt in time.    

An altar is defined as a multi-block structure with three (3) main components:   
1. The altar block - The central piece to the altar
2. The altar sign - The sign attached to the altar. Has ``[Altar]`` on the first line. Right clicking it creates the altar and allows the player to pray to the altar.
3. Candles - Light up as a status indicator to show that the altar is properly registered.

Here is an example of an altar:
![Example of an Altar](../../images/altar_example.png)

Altars are contained within a `Holy Site` which is the chunk that is defined upon the registration of an altar.   

> 📝 **Note:** The terms `Holy Site` and `Holy Land` may be used interchangeably as they are defined as essentially the same thing, the only difference is that the `Site` refers to the `Altar Block` in specific while the `Land` refers to it's encompassing chunk in general.
   
## Usage
The altar, as stated previously, serves as a marker for where and when the `Cult` was registered/formed and is the primary and direct connection between a `Believer` and a `Deity`.   

Altars have some functionality outside of being "prayer sites" as they can also function similar to the vanilla beacon, giving buffs to believers within a radius of the holy site.    

Altars will also give a base modifier when calculating reputation change of a believer and their respective deity. The current modifier is `1.5x` but can be upgraded as the cult grows and more unique believers visit the altar.

An `Offering` is an item that a player "sacrifices" to the altar by right-clicking the altar sign with an item in hand. A configurable list of items with their "value" can be found within the [config](config.md). The plugin makes a distinction between valuable/desireable items and undisreable items by assigning positive and negative values to the items. These values are then multiplied by whatever modifiers might be in effect in-order to calculate the gain or loss of reputation within a transaction.