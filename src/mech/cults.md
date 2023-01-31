> <span style="color:yellow">Currently being developed as of 2023-01-28.</span>    
   
> ⚠️ **Warning:** This page is still under construction!
# Cults
The purpose of the cults plugin is to provide another layer to gameplay. By allowing players to be creative in creating these fictious sects and design their own ideologies within the confines of the server, we open up avenues for player creativity and roleplay opportunities. As we have discussed in the introducatory pages of this documentation, increasing player engagement is one of our main goals in designing this project.

## Overview
The proposed plan for the cults system has many moving parts to it. This page was written in hopes to clarify the vision for the the plugin and its integration within the project including how it will interact with the other plugins/mechanics of the server. Each feature and mechanic of the plugin will be broken down further in this page and subsequent pages within this section.    
 
> 📝 **Note:** The terms "deity" and "god" are also interchangable and there is no difference between the two terms besides semantics.  God and deity are synonymous. According to their basic definitions, they both represent a supreme power. However, sometimes God as a term is used to represent the only supreme power, whereas deity can be used to refer to any of the forms of this supreme power and thus can be multiple in number. God is generally used in context to male gods, whereas deity can be used to refer to both god and goddess (female god).   
    
The following is a quick ten-point summary of the plugin: 
1. A player creates an [altar](cults/altars.md) in-order to pray to a deity. 
2. If the deity doesn't exist then a new religion (cult) is formed and that deity is registered, and the player who created the altar becomes the headpriest for that cult.
3. If another player "prays" to that altar and they do not belong to a cult yet, they will join that cult and become a follower of that deity they just prayed to
4. A "pantheon" can be created which is essentially a grouping of different cults/deities together. Members within a cult who are also part of a pantheon can pray to other deities within the pantheon.
5. The opposite holds true, and cults can label other cults as "enemies" or "heretics" making their deities forbidden to their worshippers
6. As time goes on and the cult gains more of a following, head priests gain more power and can set laws for their religion called "canon"
7. Canon laws can include things such as what kind of actions are forbidden by their followers such as food that is forbidden or actions that are encouraged like killing for example 
8. Followers of the cult can lose or gain favor with their god/deity
9. Head priests can appoint fellow worshipers as priests
10. Head priests and priests can pray to their deity for "miracles" or to put "curses" 

This summary, although crude, is the most simplest explanation of the plugin and how it functions. A more in-depth explanation of how the plugin works under the [Basic Usage](#basic-usage) section below.

For a better understanding, start reading from [this](cults/objects.md) page to be able to visualize the internal object classes:
> See [Objects](cults/objects.md)    

## Basic Usage
To create a `Cult` one must first build an `Altar`. Upon right clicking the sign, the plugin uses a regex-search to make sure that the deity being attempted does not match an existing `Deity` from the database. If the name is too similar or the deity already exists, it will return an error letting the user know what happened.   

If the cult is successfully created then the `Believer` (or Player) who created the cult automatically becomes the `Head Priest`. Others can join the cult by "praying" at either a `Shrine` or the altar. The head priest can promote these other believers to become priests. The `Priest` and head priest can perform prayers at the altar to grant blessings upon their cult or curses against a group of people.    

In-order to perform these rituals, a good rapport must be built with the deity. To become on good terms with the deity, the cult's believers must "pray" to the Deity (right click the sign) at shrines or altars. As relationship with the deity improves, the head priest can start to put together a `Holy Book`. 

The holy book is a set of "laws" known as `Canon` which are determined through a series of random pre-generated questions that the deity will ask the head priest. The answers given will shape the type of deity for that cult and will define what actions to take that allow a believer to either gain or lose favor.