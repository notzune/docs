> ⚠️ **Warning:** This page is still under construction!
# Objects
This page details and outlines the object classes in the plugin, attempting to give a detailed explanation of their functionality, both from a programming perspective and an in-game perspective.

## Object Hierarchy
> 📝 **Note:** This diagram is mainly just a placeholder for now but should give the general sense of the object-class hierarchy.
    
```
          ┌────────┐
          │Nameable│
          └───┬────┘
              │
              │
              ▼
         ┌───────────┐
         │CultsObject│
         ├───────────┤
         ├──────────┼┴───────────┐
         │          │            │
         │          │            │
         │          ▼            │
         │        ┌────┐         │
         │        │Cult│         │
         │        └────┘         │
         │         ▲ ▲           │
         ▼         │ │           ▼
   ┌────────┐      │ │        ┌─────┐
   │Believer├───┬──┘ └────────┤Deity│
┌──┴────────┴───┤             └─────┘
│               │
│  Believer     │
│               │
│  Head Priest  │
│               │
│  Priest       │
│               │
└───────────────┘
```

### Nameable
A simple interface to show that a class can be named, agnostic if it's a `CultsObject` or not.
```java
public interface Nameable {
    /**
     * Get the name of the specified object
     * @return A String representing the name of the object.
     */
    String getName();

    /**
     * Gets the formatted name of the object.
     * @return The formatted name.
     */
    default String getFormattedName() {
        return getName().replace('_', ' ');
    }
}
```    

### CultsObject
The `CultsObject` class is the main class that implements `Nameable`, all other object classes should extend this one.

```java
public abstract class CultsObject implements Nameable {

    String name;
    UUID id;
    protected CultsObject(String name) { 
        this.name = name; 
    }

    public void setName(String name) { 
        this.name = name; 
    }

    public String getName() { 
        return name; 
    }

    public void setId(UUID id) { 
        this.id = id; 
    }

    public UUID getId() { 
        return id; 
    }

    @Override
    public String toString() { 
        return getName(); 
    }
}
```

### Believer
The `Believer` class is a simple class that extends `CultsObject` and its main purpose is to register the player as a "believer" entity.
```java
public class Believer extends CultsObject {

    String name;

    protected Believer(String name) { 
        super(name); 
    }

    @Override
    public String getName() { 
        return name; 
    }

    @Override
    public UUID getId() { 
        return super.getId(); 
    }
}
```
### Deity
The `Deity` class also extends `CultsObject`. The purpose of this class is to represent a "deity/god" entity which is created upon interaction with an `Altar` for the first time. 

### Cult
Finally, we reach the `Cult` object. A cult takes a list of `Believers` as its members, a single `Believer` as its `Head Priest` and a single `Diety` as it's main deity (agnostic of whether it's part of a `Pantheon` or not). Believers can be promoted to `Priest`, which functions as a sort of "officer" or moderator of the cult. It also records the coords of its `Altar` and saves that as its "holy land".

### Holy Land
The `Holy Land` is the chunk containing the `Altar`. This creates a geographical "home" for the cult. This is to help track a series of cult-specific events, such as but not limited to a `Sacrafice`. 

## Transmutations
Transmutations are another aspect of `Cults` that has been planned (as of 02/10/2023) to add more depth to the system as well as incentivizing participation in the system.   

The way transmutations work is by allowing the `Cult` to be upgraded based on factors such as prayer count and `Believer` count. This rewards both active cults and large cults and keeping them as independent factors.   

Transmutations can be unlocked by only the `Head Priest` and can only be changed or modified after another succesfful upgrade. Transmutations serve as ways to enhance the player themselves through adding small modifiers to aspects such as but not limited to: 
- Jumpheight
- Movement speed
- Mining speed
- Nightvision
- Strength
    
This upgrade system is similar to the vanilla Minecraft's beacon system where modifiers can be selected based on beacon "level". The same concept is applied here for cults except that the modifiers can only be changed upon successfully levelling the cult.

<!-- ![Beacon Levels](images/../../../../book/images/beacon_levels.png)  -->
<img src="mages/../../../../book/images/beacon_levels.png" alt="Beacon Levels" width="400"/>


Instead of having players choose what race they want to pick, the “traditional” race system (dwarves, elves, etc) would be replaced with a "transmutation" (alternatively called a transfiguration, the terms can be used interchangeably in this context) mechanic that ties into the cults system. Players can therefore change their “race” by praying to different deities in-order to achieve non-human abilities (think: werewolf, vampire type “races”)

An explanation of how this mechanic could work is outlined below:

- By changing the subject of worship (deity), players are granted traits that will give them increased player attributes 
- Traits can be defined by the worshipers / Head priest: 
  - It could be spells (giving player a set of spells to cast depending on who their worship)
  - Or enhancing player’s capability: faster walk speed, higher jump height, melee damage increase, range damage increase, health increase, regen increase
  - **Special traits**: free frost walker, slows entities that you hit, free fire aspect, fire immunity, regen on hitting an entity, explode on death, see players through walls, natural armor, claws, no fall damage, short teleport
- Traits will come at a cost and the worshipers / Head priest will have to pick the drawbacks 
  - **Regular drawbacks**: slower walk speed, lower jump height, melee damage decrease, range damage decrease, health decrease, regen decrease
  - **Critical drawbacks**: burning in sunlight, golden sword, holy symbol, carnivore, can only drink blood, weak to fire, aquaphobia, unable to cast magic, intensified/constant hunger, posion weakness, can only eat metal, unable to wear armor, unable to use weapons, unable to move if being stared at, Frigophobia (take damage when snowing or standing on ice/snow)

