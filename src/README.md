# An Introduction to AirshipCraft
> v2.1.0 | 
Documentation of the mechanics and vision for the server.
---

> 📝 **Info:** This document was last updated on 2023-01-28
> 
> ⚠️ **Warning:** All information should be treated as current unless specifically told otherwise.
>
> ❓ **Looking for user guides? Click [here](placeholder).**

All information provided in this document is aimed at giving the new members of the development team as well as some existing old members some insight on what the AC:R project hopes to achieve. I will attempt to describe every single aspect of the server from it's history, it’s community, the type of players we want and attract, it’s issues over the years of past versions and attempts, it’s plans on how to fix those issues, planned features, mechanics, and gameplay, and finally it’s plans for the future in the greatest amount of detail possible. 

This is a living document. All content regarding mechanics and gameplay is subject to change as time goes on and development progresses. New things will constantly be added as they are developed.   

See the [changelog](CHANGELOG.md) to see a list of features addded/removed and/or updated.  

This project utilizes [SemVer](https://semver.org/) for its versioning structure. The correct project version number should be displayed at the top of this page and the top of the changelog.
> ⚠️ **Warning:** at thie time of writing, this document is currently in major version 0 meaning there is no playable or stable version and the project is still in initial development.  

## A Brief History

This is the second iteration of AirshipCraft. The first being mjcrafter100 (now Grau_Wulf)'s original AirshipCraft from 2015. The vision for the server was little more than an SMP server focused mainly on Movecraft and Factions nothing else. Although simple it was extremely popular and loved by many. As AirshipCraft evolved it changed to become a geopolitical server which would later be known as Total War. The Total War series of Minecraft servers will continue to face their own iterations of changes but the main focus was always some sort of land claiming plugin and Movecraft.   

The early economy system was nothing more than a few chest shops in random locations with different buy and sell prices to simulate different regional markets and to encourage players to travel around the map on “trade runs” in-order to gain money. An archaic form of a “tech tree” was implemented, using server play time and permissions as a deciding factor in what weapons or equipment a player has access to, which as you can imagine became quickly imbalanced.   

AirshipCraft: Reborn (AC:R) is similar to the original AirshipCraft in it's heavy focus on Movecraft, however that is where the similarities end.   

## Project Overview
> This will serve as an overview of the entire project. More specific topics with more in-depth explanations and plans for their implementation will recieve their own section. You can view all of these sections from the table of contents on the left of this page.

### Outline

The purpose of this project is to fulfill the vision of creating a "true" geopolitical experience in Minecraft. Although it is not based on an Earth map, the map is Earth-like enough to encourage the natural growth and creation of nation states through either player or NPC manipulation. "Dynamic" is the key buzzword for this project.   

The world, much like real-life, should feel fluid and constantly changing. Changing market prices due to inflation and supply and demand patterns, wars and diplomatic actions by foreign nations, natural disasters that effect multiple aspects of life, etc. All of these are examples of things that this project attempts to replicate in the virtual world. 

A primary focus of this project is the concentration on NPCs and heavily involving them in game mechanics. This is to keep gameplay constantly interesting as they (theoretically) serve many advantages to our goal.  

With NPC controlled nation states scattered across the map, there will constnatly be something for the player to do. In theory the server should be fun and playable even if the player is completely alone on the server.   

The goal of the economy is to be player-driven. There should be enough incentive for players acquiring currency without it being too much of an obstacle and therefore potential deterrant for new players. Finding a good balance is difficult but not impossible. 

> See [Economy](mech/economy.md)

We want to provide a server where realistic stratagem, tactics, and creative thinking will allow players to get ahead. We want players to be able to have and control their own fully functioning and dynamic nations, towns and empires. We want to find the balance between complexity and simplicity. Allowing for in-depth and complex mechanics but still being extremely player and noob friendly but still being able to provide a steep enough learning curve to separate the good players from the amateurs in more aspects than just raw Minecraft skill. 

Although AirshipCraft was never traditionally marketed as a “roleplay” server (and still technically isn’t), we are taking steps to emulate a kind of “roleplay” environment to immerse players in this new world we are building. This includes the writing of lore, the creation of a quest system, player cards and other things that promote roleplay. Roleplay is highly encouraged but we will not enforce it and allow it to occur naturally.

### Game Design

The project is designed with the mindset of building a game. The goal is to design and implement gameplay elements that foster player engagement and boost player retention. Althoguh the server is designed so it could be fun without being populated, it's more beneficial for all parties if there is a sustained playerbase.   

This graph outlines a player’s skill vs. difficulty.  
![Skill Vs. Difficulty](images/skill-vs-difficulty.webp)

Note this shows three difficulty levels and how players react to it based on their skills. Also note that the blue line enters all three boxes, which is important to get the most players interested in the gameplay.

By itself, this means nothing. However, combine it with this graph:

![Player Interest/Efficacy](images/interest-and-efficacy.jpeg)

This shows that in the median, player interest is tied to efficacy. In other words, the better you are at something, the more you’re interested. The interest drops off according to standard deviations from the median difficulty line shown in the first graphic.

The full meaning of both of these graphs isn't realized until we look at this next graph:

![Difficulty and Challenge](images/difficulty-challenge-graph.jpeg)

This shows that as you move across difficulty levels, you engage players. This implies you have a game that can watch a player’s reactions and scale difficulty based on their performance. The AI needs to constantly move between the optimal challenge line, the blue line in the first graph. It is based on these assumptions:

1. **One cannot design a difficulty that is perfect for everyone.**
2. Therefore, we must move the player above and below the difficulty line using Rewards.
3. The best way to do this is to provide multiple reward types that cater to different styles of play.

Rather than categorize players as high skill vs. low skill, attenuate the game to make players feel high skilled and low skilled. Both levels serve a purpose, as graph 3 shows. Note that the stuff in the quotation marks in graph 3 are the negatives of this mode.

Given this, we think of the following as guiding principles:

- As players move above the optimal challenge line, they feel high satisfaction.
  - Keep them there too long and they quickly devolve to more negative feelings of the play being ‘too easy’ or ‘childish’.
- As players move below the optimal challenge line it leads to high player effort to succeed.
  - Here the positive emotions of challenging and exciting are balanced by the negative pitfalls of it being ‘too hard’ or ‘frustrating’. You can’t keep them here too long either.
- The key to successful engagement is to move players across this line using a rewards system that caters to both high satisfaction (ranks, levels, recognition, Right Brain motivators) and high effort (items, upgrades, bonuses, Left Brain motivators).
    
And finally, again:
- **No two people are the same**, so there is no true ‘optimal challenge line’. It is a construct used to understand from measurement when to make hurdles harder or easier based on individual player performance.   

This is one way to deal with player engagement and create addiction. Great games closely adhere to the ‘Optimal Challenge Line’ as created by each player’s skill and use the Octalysis drivers to push players back and forth across the line.   

Octalysis is a great breakdown of player motivations by Yu-Kai Chou. We can use the drivers here to motivate high satisfaction and high effort players, as each respond to different things.    

This is beautifully captured in this graphic:
![Octalysis of Gamification](images/gamification.jpeg)

The graph is a very good guide on what should be kept in mind when proceeding with development of the server/project. We can however, for sake of simplicity, focus on mainly the key points of the graph.

- **Progress**: 
  - As they advance in the game, players should feel a sense of accomplishment. Clear objectives, like leveling up different skill or techtrees or unlocking of new items or abilities, or things such as making the world more "exploration worthy" can help achieve this.
- **Feedback**: 
  - Players must receive immediate feedback on their actions, such as points earned or money earned, in order to improve gameplay and keep them engaged.
- **Difficulty**: 
  - The game should be challenging enough to be engaging without being too difficult to the point where players give up in frustration.
- **Social**: 
  - To encourage players to compete with one another, the game should have a social element like leaderboards or some sort of way to give players "bragging rights" but also making those bragging rights worthy of being saught out.
    - An example could possibly be the [cults](mech/cults.md) system, or the [nodes](mech/nodes.md) system.
- **Replayability**: 
  - The game should entice players to return and play it repeatedly. Randomly generated content, immersive and dynamic world, and other event-like activities and objectives can help accomplish this.

A good storyline can engage players and make them want to keep playing to see what happens next. We aim to acommplish this by providing multiple quest lines that have benefits and impacts on the player who chooses to complete them and possibly (slight) drawbacks to those who don't in-order to gently nudge players to keep playing and trying different things.

### Philosophy
It's important to maintain a common shared philosophy when designing or working on mechanics. The general mantra is to add quality of life (QOL) improvements to the player whenever possible. If we are able to streamline the boring, basic, vanilla mechanics and make it very easy, or in some cases automated, for the player: the player can focus on the unique, more interesting and "fun" mechanics we have designed for them.   

If a player sits and has to mine or farm for resources manually for everything they need then they will only spend about 1/4th or less of their time actually playing the game since 3/4ths of it would be spent grinding. **Try to limit uneccessary grinds.**    

Designing any sort of progression system or mechanic that requires players to put in effort is **good** (as we have stated before in the previous section), however, there's a difference between challenging and time consuming and we want to limit time consuming whenever possible. 

### Purpose of These Docs
This documentation serves as a guide to potential/future developers who have graciously volunteered or have been brought on to the team to work on AirshipCraft.   

Planned features which are outlined and explained in any of the subsections to the left of this page might include a note at the top of the page such as: 
> <span style="color:red">Currently unimplemented.</span>
      
> <span style="color:green">Implemented as of YYYY-MM-DD.</span>
    
> <span style="color:yellow">Currently being developed as of YYYY-MM-DD.</span>

These notes give a sort of status indication of what features have been added, which are currently being worked on, and what features have not been implemented at all.

---
**Written by**:   
Zeyad “zune” Rashed,  
Head Developer and Project Manager  
AirshipCraft  
AirshipCraft: Reborn  

**Contact**:    
[Website](https://www.airshipcraft.tk/) (Homepage)  
[Discord](https://discord.gg/E287MWbVUK) (Discord)    
[GitHub](https://github.com/notzune/docs/issues) (GitHub Repo)