# Combat
> Authors: [Locutusque](https://github.com/Locutusque) and [SupremeNoob](https://github.com/eerieXanthic)
    
Massive overhaul to how combat will be handled on the server. Throws default vanilla META out the window and instead introduces a robust new system.

> A frankenstein monster I have created taking inspiration from various games. [Transmutations](cults/transmutations.md) are not mentioned too much but should go fine with the proposal.
> - SupremeNoob

## Damage Types
In-order to differentiate armor types an weapon types and to make each one unique in its own way, we will be introducing different damage types. Each different damage type can be countered by something else so it adds a fun and interesting layer to combat especially since you can set up your loadout depending on the kind of item "synergy" you want.

> See [Damage Types](combat/damagetypes.md) for a list of all damage types.
   
## Protection, Speed and Penetration
### Protection
Each type of armor will give different protection depending on the toughness of the armor in vanilla. (*The detailed numbers are yet to be determined.*)
    
- The higher the toughness, the higher your protection becomes, and the slower you will move
- Protection, speed and penetration are all percentage numbers
- The base speed of a player will be increased to make sure that having heavy armor doesn't slow the player down too much/ does not go lower than vanilla movement speed.

### Penetration
Unprotected damage = 100% + ( (Penetration - Protection) 
    
Unprotected damage will not go high than 100% and lower than 0%
    
For example, leather boots give you 10% protection, iron pants give you 30%, diamond chestplate gives you 60%, netherite helmets give you 40%.
    
`Total of protection` = 10% + 30% + 60% + 40% = 140%
    
If you are being hit with a penetration value of 30%:
    
`Unprotected damage` = 100% + 30% - 140% = -10% = 0%
    
If you are being hit with a penetration value of 150%:
    
`Unprotected damage` = 100% + 150% - 140% = 110% = 100%
    
Weapons will have their own penetration value for each of their moves, affected by the artifact modifiers.
    
Heavy attacks will grant the weapon an extra 50% (affected by the artifact modifiers) penetration, while light attacks will have bonus on penetration (also affected by the artifact modifiers).

### Speed
Speed currently only affects movement. If the movement speed is not enough to dodge entities’ attack and speed builds turn out too weak, a dodge and accuracy mechanic can be implemented, but that is to be determined.
    
## Weapon Total Damage Calculation
Here we will discuss how damage will be calculated.
    
### Critical Hit
All weapons will have a base crit chance of 5% and a base crit damage of 200%
    
This can be increased with artifact modifiers.
    
### Total Damage
    
`Weapon Total Damage` =     

( (`Base Damage` * `Special Damage %`) + Bonus from [Transmutations](cults/transmutations.md)) * `Crit` * `Unprotected Damage`

> Note for clarity: Critical damage is **only** factored in on a critical hit.
> "Special Damage" refers to the damage from a weapon's special move.

## Damage Composition
The damage composition is affected by element convert value, which is a percentage (0% - 100%).

After calculating the weapon total damage, it will split into two:
   
1. **Physical damage** = Weapon total damage * (1 - Element convert value)
2. **Elemental damage** = Weapon total damage * Element convert value

## Damage Weakness
The final damage is affected by how weak the entity is to the damage type.
    
Weakness will be a percentage:
   
- At 100%, the entity will take full damage
- At 200%, the entity will take double damage 
- At 50%, the entity will take half damage
- At -100%, the entity will be healed using the full damage value

## Final Damage Calculation

`Final Damage` = (`Physical damage` * `Damage Type Weakness`) + (`Elemental damage` * `Damage Type Weakness`)

## Status Effects
Status effects will have a chance to proc, which depends on the damage composition of the weapon.
    
Proc chance = Element convert value
    
Proc damage = Weapon base damage * Weapon proc damage * Damage Type Weakness
    
Weapon proc damage will have base percentage of 5%, which can be increased with artifact modifier.
    
## Final Thoughts

This proposal will massively increase the scope of the project. Expect ~8-12 artifacts (4 x 8 or 4 x 12 = 32 or 48 moves) or less at launch. More people can join to help make more artifacts, but it will also increase the balancing work.

> See [Artifacts](combat/artifacts.md)