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