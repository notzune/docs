# Claiming System
The claiming system, as mentioned in the [Nodes](nodes.md) page, will be essentially a fork of [Towny](https://github.com/TownyAdvanced/Towny) with a few elements from other plugins.

If you are not familiar with Towny then to put it simply, it is one of those claim management plugins that allows players to claim land that other players can not access, break or modify and also allows players to invite other players to a “group” that has access to said land so that way only people within the group can use that land.

In vanilla Towny, there exists something called “Objects”. Objects can be defined as one of a few things, and follow a hierarchy:
1. Resident (Player) - The lowest level of object.
2. Town (Group of players, lead by a “mayor”)
3. Plot (Chunk that is owned by a resident or Town)
4. Nation (Group of towns, led by a “king”, all towns within a nation can modify other towns within the same nation. Nations can ally and enemy each other and wage war with one another)
> Developer Note: See [TownyObject.java](https://github.com/TownyAdvanced/Towny/blob/master/src/com/palmergames/bukkit/towny/object/TownyObject.java)

   
Our claiming system plans to expand on Towny by using it as a base template and combine it with a system such as [nodes](nodes.md) and integrate it with our [economy](economy.md) and the [cults](cults.md) system.   

## Why other systems kinda suck:

Factions was just straight up never good for these kinds of servers.

Towny puts too much focus on the "homeblock", or the capital, of their towns (the basic land claiming unit). So an entire nation has it's heart at a single chunk that is 9 out of 10 times the town who created the nation in the first place. In-order to move the capital of the entire nation, say to somewhere more strategic, you would basically have to give up ownership of the town in-order to make another town the "capital" and therefore have that mayor (the person who is in charge of the town) be king.   

In pretty much all of Towny's warfare systems, if you take out the homeblock you win the war.   

In Towny, wars are either too fast (the flag-war system, the attrition system which was kill based) or wayyyy too slow (modern Siege sytem)

The brightside of Towny is that it's constantly being updated by competent developers, and those developers are also very helpful when it comes to adding new features using their API and will sometimes even lend a hand in development.

I believe that Towny is a good base for our new hybrid claims system because of this reason alone, not tom ention it already has the basic object hierarchy structure that we can work off of. 