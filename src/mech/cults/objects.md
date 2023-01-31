# Objects
This page details and outlines the object classes in the plugin as well as attempting to give a detailed explanation of their functionality, both from a programming perspective and an in-game perspective.

## Object Hierarchy
> 📝 **Note**: This diagram is mainly just a placeholder for now but should give the general sense of the object-class hierarchy.
    
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
A simple interface to show that a class can be named, agnostic if it's a CultsObject or not.
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
    protected CultsObject(String name) { this.name = name; }
    public void setName(String name) { this.name = name; }
    public String getName() { return name; }
    public void setId(UUID id) { this.id = id; }
    public UUID getId() { return id; }
    @Override
    public String toString() { return getName(); }
}
```

### Believer



