> <span style="color:red">Currently unimplemented.</span>
# Claiming System
The claiming system, as mentioned in the [Nodes](nodes.md) page, will be essentially a fork of [Towny](https://github.com/TownyAdvanced/Towny) with a few elements from other plugins.

If you are not familiar with Towny, then to put it simply, it is one of those claim management plugins that allows players to claim land that other players can not access, break or modify and also allows players to invite other players to a “group” that has access to said land so that way only people within the group can use that land.

In vanilla Towny, there exists something called “Objects”. Objects can be defined as one of a few things, and follow a hierarchy:
1. Resident (Player) - The lowest level of object.
2. Town (Group of players, lead by a “mayor”)
3. Plot (Chunk that is owned by a resident or Town)
4. Nation (Group of towns, led by a “king”, all towns within a nation can modify other towns within the same nation. Nations can ally and enemy each other and wage war with one another)
> Developer Note: See [TownyObject.java](https://github.com/TownyAdvanced/Towny/blob/master/src/com/palmergames/bukkit/towny/object/TownyObject.java)

   
Our claiming system plans to expand on Towny by using it as a base template and combine it with a system such as [nodes](nodes.md) and integrate it with our [economy](economy.md) and the [cults](cults.md) system.   

## Why other systems kinda suck:

Factions were just straight-up never good for these kinds of servers.

Towns put too much focus on the "home block", or the capital, of their towns (the basic land-claiming unit). So an entire nation has its heart in a single chunk that is 9 out of 10 times the town that created the nation in the first place. To move the capital of the entire nation, say to somewhere more strategic, you would have to give up ownership of the town to make another town the "capital" and, therefore, have that mayor (the person who is in charge of the town) be king.   

In pretty much all of Towny's warfare systems, if you take out the home block you win the war.   

In Towny, wars are either too fast (the flag-war system, the attrition system which was kill-based) or wayyyy too slow (Modern Siege System).

The bright side of Towny is that it's constantly being updated by competent developers, and those developers are also very helpful when it comes to adding new features using their API and will sometimes even lend a hand in development.

I believe that Towny is a good base for our new hybrid claims system on this basis. Not to mention, it already has the basic object hierarchy structure that we can work off of. I believe [phonon's nodes](https://github.com/crusalis/multi-nodes) would not be an acceptable base for our fork as it is way too bare bones compared to Towny and removes necessary features that we can use to expand off of, such as the different ``plot-types`` built in the Towny API. Not to mention that the source for phonon's nodes is written in Kotlin which will make collaboration significantly harder as it's currently not a widely accepted language standard for plugin development. 

## Why the fork is necessary:

Forking Towny is necessary as it plans to offer better implementation of certain gameplay features that vanilla base Towny can't offer as it would be too niche for them to consider. Features such as:

- Direct support and integration of the proposed [nodes](nodes.md) system.
- Integration for the [cults](cults.md) mechanic.
- Better integration with Movecraft.
- Direct integration for proposed [NPC](npc.md) mechanics such as: 
  - Spawning of [soldiers](npcs/types/soldier.md).
  - Implementation of proposed mechanics of NPC nations.
- Better [permissions](nations/permissions.md) system

## Concept Overview
The proposed nations system aims to be as dynamic as possible and gives the player as much freedom as possible when structuring their claims. Since the project aims to be a geopol, a proper, well made nations system is crucial for the project to succeed. As stated above, this system aims to integrate directly with the NPCs as a way to implement NPC specific event triggering and a sort of "diplomacy algorithm" to handle inter-player and non-player interactions.   

Land claiming is just the basics of the nation system but the real magic lies in its object structure and unique permission based land management. With the permissions system, roles such as Governor, Treasurer, General, etc. will no longer just be "roleplay" but actually coded into the game.   

Introduction of the plot system is not a new concept as it was done in Towny where nations/towns can set certain chunks as a different plot-type, each with their own special attributes. One such example is a jail plot that supposeduly would allow for the imprisonment of rival players. This feature was buggy and the towny method for implementing plots wasn't very straightforward and was barely beneficial for the casual player.   

This new system attempts to fix that by tying plot-types to other plugins such as perhaps a factory plot that can tie into Movecraft or a [bank plot that ties into the economy](../economy/banking.md). The plot-type system adds a way for other plugins to hook directly into our nation system by allowing for unique event triggers and more intuitive location-based event firing. 

> See [Objects](nations/objects.md) and [Permissions](nations/permissions.md)
    
### Warfare
