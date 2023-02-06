# Housekeeping Rules
This page goes over some basic housekeeping rules in-order to maintain efficiency and organization within the project as well as instating some general guidelines about maintaining, contributing to, and using the project.

## Merge Conflicts and Prevention
> Version control systems, like git, auto-magically manage code contributions. It identifies the change, when it occurred, who made it, and on what line so that developers can easily track the history of their codebase. However, git sometimes gets confused in the following situations:
> 
> - When more than one person changes the same line in a file and tries to merge the change to the same branch
> - When a developer deletes a file, but another developer edits it, and they both try to merge their changes to the same branch.
> - When a developer deletes a line, but another developer edits it, and they both try to merge their changes to the same branch
> - When a developer is cherry-picking a commit, which is the act of picking a commit from a branch and applying it to another
> - When a developer is rebasing a branch, which is the process of moving a sequence of commits to a base commit
>
> *Taken from a [Dev.to](https://dev.to/github/how-to-prevent-merge-conflicts-or-at-least-have-less-of-them-109p).*
   
This can be extremely frustrating especially on a project such as this when there will be times where more than one person may be working on a specific piece of code. 

Luckily we can take several steps to prevent this from happening: 
### Standardization of Formatting
When developing in Java, many developers have different styles of coding. In-order to standardize here are some guidelines that you should try and follow to keep code uniform and to prevent preventable merge conflicts on PRs: 

#### **Whitespaces** 
This is a big one. Make sure there is a white space between each new method such as:
```java
public class Example {
    // whitespace
    public Example() {
        //some code...
    }
    // whitespace
    public void anotherExample() {
        //some code...
    }
}
```
Add white spaces to make code more readable such as this example from [TechnoVisionDev/JDA-Tutorial](https://github.com/TechnoVisionDev/JDA-Tutorial):

*Instead of doing this:*

```java
public class TutorialBot {
    
    public TutorialBot() throws LoginException {

        // Build shard manager
        DefaultShardManagerBuilder builder = DefaultShardManagerBuilder.createDefault(token);
        builder.setStatus(OnlineStatus.ONLINE);
        builder.setActivity(Activity.watching("TechnoVisionTV"));
        builder.enableIntents(GatewayIntent.GUILD_MESSAGES, GatewayIntent.GUILD_MEMBERS, GatewayIntent.GUILD_PRESENCES);
        builder.setMemberCachePolicy(MemberCachePolicy.ALL);
        builder.setChunkingFilter(ChunkingFilter.ALL);
        builder.enableCache(CacheFlag.ONLINE_STATUS);
        shardManager = builder.build();

        // Register listeners
        shardManager.addEventListener(new EventListener(), new CommandManager());
    }
    ...
}
```
*Do this:*
```java
public class TutorialBot {
    
    public TutorialBot() throws LoginException {

        // Build shard manager
        DefaultShardManagerBuilder builder = DefaultShardManagerBuilder.createDefault(token);
        builder.setStatus(OnlineStatus.ONLINE);
        builder.setActivity(Activity.watching("TechnoVisionTV"));
        builder.enableIntents( // add whitespaces here to make it more readable
            GatewayIntent.GUILD_MESSAGES, 
            GatewayIntent.GUILD_MEMBERS, 
            GatewayIntent.GUILD_PRESENCES
            );
            ...
        shardManager = builder.build();

        // Register listeners
        shardManager.addEventListener( // add them here too
            new EventListener(), 
            new CommandManager()
            // this also makes it easier if you were to add more things to the list later on
            ); 
    }
    ...
}
```
