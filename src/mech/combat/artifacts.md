# Artifacts
> Authors: [Locutusque](https://github.com/Locutusque) and [SupremeNoob](https://github.com/eerieXanthic)
    
> See [Artifact List](combat/artifact-list.md) for a full list of items with descriptions.
    
Artifacts are special items on this server, in the form of weapons or armor. The weapon could be a sword, an axe, a bow, a gun (musket/rifle), a wand, etc, while the armors are randomly generated.
    
The damage type of the weapons can be switched by the players. Changing the projectile color/block in the process.
    
Players are limited to equipping/attuning 2 artifacts.

## Weapons Design Philosophy:
Each weapons will be given 4 types of moves, each triggered with left clicks, shift left clicks, right clicks and shift right clicks.
   
For a `melee` artifact:
- Left click: Light melee attack
- Shift left click: Heavy melee attack
- Right click: Movement/defense utilities
- Shift right click: Special move
For a `range` artifact:
- Left click: Movement/defense utilities
- Shift left click: Special move
- Right click: Light ranged attack
- Shift right click: Heavy range attack
For a `magic` artifact:
- Left click: Light spell attack
- Shift left click: Heavy spell attack
- Right click: Movement/defense utilities
-Shift right click: Special attack
For a `hybrid` artifact:
- Left click: Light melee/ranged/spell attack
- Shift left click: Heavy melee/ranged/spell attack
- Right click: Movement/defense utilities
- Shift right click: Special attack
    
For melee/magic/hybrid weapons, light and heavy attacks are mostly on left click and right click respectively. These are switched with right click and shift right click with range weapons (Bows/Crossbows)
    
Each move will give a cooldown (CD) for the weapons. No other moves can be used if the cooldown is not over.
    
To perform a special move, the player needs to fulfill some special requirement. Before using the special move, the weapons may need to:
    
- Be charged with left clicking 
- Hit an enemy with 3 light/heavy attack 
- $etc...$

## Damage of each move
The damage of each move will be represented with percentage, here is 4 moves for example:
   
1. Left click: Triggers a light melee attack that deals 70%
2. Shift left click: Triggers a heavy melee attack that deals 150% damage
3. Right click: Triggers a short leap (Deals no damage)
4. Shift right click: Shoot a projectile that deals 250% damage
    
If the base damage of the weapon is 10, the moves would respectively deal: 
    
1. 10 * 70% = 7 damage
2. 10 * 150% = 15 damage
3. No damage
4. 10 * 250% = 25 damage

## Artifact Modifier
Each artifact will have their base stats, but also come with 1 - 3 random modifiers that gives buff to the player/item:
    
- Buffs:
  - Decreased Heavy attack cooldown
  - Increased multishot
  - Increased heat damage
  - $etc...$
    
But with more than one buffs comes debuffs, it could be a single massive debuff or multiple small debuffs:
    
- Debuffs:
  - Decreased Heavy attack damage
  - Decreased range
  - Increase cold weakness
  - $etc...$

The armor modifier and the weapon modifier will stack together.

## Weapon Element
Weapons will have a randomly applied element to it. It will also have an element convert value attached to it (0% to 100%). This will affect how much of the damage is converted into the element of the artifact as well as the status effect proc chance.
    
> See also [Damage Composition] and [Status Effect].

# Player Progression
Player progression is an important core concept of the project as outlined on the [introductory pages](../README.md). 
## Obtaining Items:
There shall be ruins and dungeons scattered across the map. Inside these structures are chests, and inside these chests are armor/weapons/riches. 
    
Dungeons are to be determined, but here is my suggestion for ruins:
   
1. Players explore the map for ruins
2. Players could start a raid on the ruins by entering it
3. Custom mobs starts spawning as soon as the raid begins
4. Players can crack open a chest by clicking it, but have to stay for a certain period of time until it opens, spawn rate increases
5. Players can leave the ruins to end the raid at any time

## Deconstructing items:
Weapons and armor can be deconstructed into predefined/random materials:

- Iron
- Diamonds
- Redstone
- Bones
- Other tradable items... $etc...$

This will get rid of the players’ unwanted artifact and grant them resources, but also give an artifact component that can be used to reroll artifacts.

## Modifying items
Artifacts can be rerolled with artifact components. Changing its modifiers into another group of random modifiers. 
    
Players can also use artifact components to reroll the element to get a more ideal element or damage composition.

## Gameplay Loop
This proposal can create a gameplay loop in which:

1. Players look for cheap cargos to buy.
2. Players leave on an airship and head to a destination city
3. On the way players can look for ruins/dungeon on the ground
4. Raid the ruins for items
5. Extract with the goods via their airship
6. Arrive at the destination city and sell the cargos
7. Deconstruct the unwanted items and equip their new items/reroll their old items
8. Repeat
    
Could be a little bit of a grind but I highly recommend having this system (+ [transmutations](cults/transmutations.md)) instead of a regular leveling system since having level difference can have a massive balancing issue in a server that simulates geo politics. This way, players can at least get combat ready gears in a short time, only to grind for combat optimized gear when they are ready.
    
To reduce the grind, we can introduce these mechanic:
   
- During reroll, we can allow players to keep the original modifiers after rerolling.
- While opening a chest in raid, we can allow players to choose if they want helmets, chestplate, pants, boots or a weapon.

### **Problem**
It could be little to no time before the market is saturated with artifacts, therefore we might need to:

1. Force the players to store the artifact in a special storage, limiting the number of artifacts a player can have 
   - The number of artifact slots can be scaled with how many items we have implemented in total
2. Instead of giving the artifacts straight away, give an “artifact token” instead, players will go back to town and trade the token for a random artifact (Others can kill the player to take the token for themselves)
3. If a player runs out of artifact slots, they can choose to immediately deconstruct either the new item or an old item they have.

With these mechanics, we should be able to allow free trading between players with artifacts. Of course, the most ideal situation is that we have enough variety for artifacts to not be saturated easily.
    
Alternatively, we can do this instead:
    
- Artifacts can have custom durability abd can only regain a certain amount by sacrificing the same type of artifact
    - Reaching 0 durability will not break the item, only making it temporarily unusable
    - This can have a constant drain on artifacts, creating a demand in the market

This would create artifact merchants within the player base and there should be no need to limit the number of artifacts a player can have.