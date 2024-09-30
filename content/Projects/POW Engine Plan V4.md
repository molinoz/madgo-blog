POW is an engine to for users to create and play board, card, and ttrpg games online without to know how to code. It will still be a process that they would need documentation for. But it will be more accessible then having to create it from scratch.

My biggest motivation for this project is the amount of features to work on. This project has required everything I have learned. It also has been letting me know what lessons I have neglected and need to review.

The main focus is TTRPG games due to their market value. Also all their needed features overlap with board and cards.

Also a hopeful side effect is to grow interest to other TTRPG games besides DND. Along with creating a better market for indie game developers.

The whole design philosophy is for users to create their own content not us(even though I will to test things out)
> # Base Product Plan
> ## Similar Products and Inspirations
- [Tabletop Simulator](https://www.tabletopsimulator.com)
- [Roll20](https://roll20.net)
- [Foundry](https://foundryvtt.com)
- [GCS](https://gurpscharactersheet.com)
- [COMP/CON](https://compcon.app)
- [chess.com](https://www.chess.com)
## Benchmark Games
These are games that POW aims to be able to run, and aid
### TTRPGs
#### Custom TTRPG Malum
[Malum](https://sites.google.com/view/malum-test/rules-compendium) is a TTRPG my friend Gavin has been working on and running. It is in its first stages and the actual test is if Gavin can set it up in POW on his own.
#### Secondary Games
These are TTRPG games I plan to run to test out but are not priority but help cover use cases.
- [Path Finder:](https://paizo.com/pathfinder) A game like Dnd which also has a high fantasy setting
- [Mutants and Masterminds:](https://greenroninstore.com/collections/mutants-masterminds) A unique power building system to use for a Superhero setting
- [Lancer:](https://massifpress.com/lancer) A system built for mech combat with a list of mechs to choose from.
#### G.U.R.P.S.
The [Generic Universal Role Playing System](https://www.sjgames.com/gurps/) is more like a toolkit to create custom games systems powered by GURPS. 
It's goal is to be able to use it for any setting.
If POW gets to the point where GURPS is a good game aid then it can be that for any system.
### Board Games
#### Fairy Chess
It is a [variant of chess](https://en.wikipedia.org/wiki/Fairy_chess) with custom pieces that have there own movement. Linking data to tokens/cards/pieces is a major focus for pow and creating custom pieces for fairy chess would be fun.
#### Supremacy
Is a [strategy board game](https://en.wikipedia.org/wiki/Supremacy_(board_game)). Gav has setup. It is an updated version which is a mashup of different expansions and variants of the original game. Its basically its own game now.
It requires some accounting which was hard to keep track of. I personally handled it by creating a [Google sheet](https://docs.google.com/spreadsheets/d/1i3NC7c1G-6Om7rvBP2G5hsiAC4aUVkf3pyiAfMqJz-w/edit?usp=sharing). This how my sheet ended up looking at the [end](https://docs.google.com/spreadsheets/d/1gpeOIeqatTMNH_PAKaUGKE97cqLEFgN_BC52KC2szyE/edit?usp=sharing).
### Card Games
- ***Custom Crazy 8s***(UNO)
- ***Poker***
## Vocabulary
***Orb:*** The game environment that holds all the assets, statblocks, and other custom content. This is an Orb instead of world to prevent confusion with world building lingo. Which is to describe creating and setting up content.
That way when someone is talking about world setting or building. They are talking about the setting(the location in which campaigns story takes place).
While Orb building and settings are how you set up and organize the content and players in the orb.
***Layout:*** A Custom Character sheet or UI Component that can manipulate the data of an object.
***Object:*** A data object connected to a piece on the board or layout that manipulates it data.
***Statblock:*** A TTRPG term for a document that has an NPC or PC's stats and information. 
***Content:*** Lore Notes, Art assets, Rules, and Statblocks
***Module:*** A premade adventure or setting that can run through with a rule system. In POW it will be a term for how your Orb is set up. You can share the Orb with what content it uses and how it is set up as a module other people can play and run.
## Engine Features
### Object Editor *currently working on*
An editor to setup the structure of a data object. Currently Data is saved in json files so you can just write it in json if you know what POW needs for it to work. 
A form based on the data object lets you add, remove, rename, and set values to properties. This makes the process easier and a quick start off.

Currently working on it. It is easier to show how it looks when it completed rather then explain how to do it.
#### Example
```json
{
    "type": "data",
    "sheet": {
	    "name": "PC Sheet",
	    "version": "0"
    },
    "info": {
        "img": "",
        "name": "",
        "player": "",
        "creator": "",
		"level": "",
		"playerArchetype": "",
		"playerSubtype": "",
		"size": "",
		"organizations": [],
		"allies": [],
		"enemies": [],
        "culture": [],
        "backstory": ""
    },
    "tracker": {
        "wellness": {
            "current": 0,
            "fieldMax": 0,
            "max": 0,
            "hpi": 0,
        },
        "defense": {
            "total": 0,
            "base": 0,
            "deflect": 0,
            "toughness": 0,
            "dr": 0,
            "multipliers": []
        },
    },
    "inventory": {
        "currency": 0,
        "weight": {
            "weightedCurrency": false,
            "current": 0,
            "capacity": 0,
            "encumberance": 0,
        },
        "items": [
            {
                "name": "Equiped",
                "weight": 0,
                "reductions": "80%",
                "capacity": 0,
                "items": {}
            },
            {
                "name": "Bag",
                "weight": 0,
                "reductions": "50%",
                "capacity": 15,
                "items": {}
            }
        ]
    }
}
```
### Sheet Editor *currently working on*
This was the first part of the project I have been planning out. I decided to sacrifice visual customizability and creativity for simple and useful. I have created a custom component called an `<Infoblock/>`. Where I can input a hierarchy of objects and it will render them based on the data using a list of components.
#### Simple example
```json
name: "",
//... any additional properties can be added
infoBlock: {
	type: "container", // category of components due to similar functions needed
	form: "booklet" // the specific component needed
	//... additional properties that contain settings on how it behaves and where you give it info it needs like 
},
children: [] // Container components have children that are for containers additional infoblocks to be rendered. Another example are Dropdowns where the children are not infoblock but a list of objects that are its options
```
### Wiki-like Collaborative Note Taking
I have been using [Obsidian](https://obsidian.md) for note taking for a long while now and I really like how they do it over google docs and word. Using a [syntax similar to obsidian](https://help.obsidian.md/Editing+and+formatting/Basic+formatting+syntax) would be better then setting up a UI to do the same thing.

What POW could do is be able to hide sections of a note and be able to dictate who is able to see it. This will let game runners write everything into the orb. They won't have to worry about spoilers for their players. It can work along side the permission system. Which will be elaborated on in the _Social Features_ section of this document. Or by inputting the username of those who are aloud to see it.

It would be cool if the system notifies users when they gain access to new info.
### Board Editor
This is the code to handle all the interactions between objects. 
This might be the most complex with a lot of use cases.
##### Turn Tracker
The Turn tracker is a list of cards. They represent the objects on the field. A player can select who on that list to attack and do actions to. This will be the core for every type of board.
##### Custom Pop ups
I still need to write it out properly. But, basically, the same way as in "Baldur's Gate 3." You need to roll for something, so a popup appears. When you open a loot container, a popup appears to grab what you want. When buying from a shop, etc. The sheet editor should be able to make the contents of those popups. The question is how to set how they popup.
#### Turn Board
Not really sure what to name it but the idea is for RPG combat screens Like Pokémon or Earthbound. Where there are only a background image the sprites of who is in combat and then being able to select who to hit.
##### Example
![pokemon|250x175](https://miro.medium.com/v2/resize:fit:640/format:webp/1*baExuvv8c4jybSXRoYbj9A.jpeg) ![earthbound|500](https://i.redd.it/wrx2j1jhlt8b1.png)
#### 2d Board: Tile Maps
Objects connect to a movable, targetable sprite. Other objects can interact with it. They can move freely or on a grid. There are 2.5 types of grids the conventional square grid and hexagonal/isometric.

I lump hex and iso together. When I tried to figure out how to set up an isometric grid in Roll20, I found the isometric grid was behind a paywall. I got around it because an isometric grid overlaps perfectly on an invisible hex map.
![|500](https://i0.wp.com/2minutetabletop.com/wp-content/uploads/2021/08/Isometric-grid-overlay-demonstration-on-Roll20.jpg?w=795&ssl=1)

One of the features that can differentiate us from other virtual tabletops top are *areas of action*. In chess.com and other online chess games, when you click a piece, its valid move spots change color. Clicking on a spot moves the piece there.
This feature will do well for any board game. It just needs to cover more use cases for TTRPGs. Specifically, it should address attack range, AOE, and other factors.

Another thing is hiding part of the map that the characters can't or shouldn't be able to see.
- Fog of War: A layer that can be "painted" to cover unseen areas ![|500](https://keithburgun.net/wp-content/uploads/2017/04/post-11-1401887350-1024x576.jpg)
- Sight Cone: A more adaptive fog of war where the game runner doesn't not to paint and remove it. The closets example, but a very advanced one, is [Project Zomboid](https://store.steampowered.com/app/108600/Project_Zomboid/). Roll20 has a similar feature in their premium plan for"[Dynamic Lighting](https://help.roll20.net/hc/en-us/articles/4403861702679-How-To-Set-Up-Dynamic-Lighting#Building-Your-Map)"
- Fixed View: Just setting up a maximum zoom out around a character
##### Examples
###### Square
![moonring|500](https://img.itch.zone/aW1hZ2UvODU1ODAzLzQ4MDExNTYucG5n/original/uYCQx9.png)
![FE](https://lh3.googleusercontent.com/proxy/dbus9Kf0UtIPgrMZxUKM-m3-W2lx8EFMKqHgtcoGUBFqOcF--2nsDWTt6dbwrIqaeVtlx9-AgLmgMlmCYncw20sW-Djn3RFVi4OtPN4S2yqHJyr9q3q2BZE)
###### Hexagonal
![lancer|600](https://img.itch.zone/aW1hZ2UvMTAwNjI0MS84MTI3MjExLnBuZw==/original/57waly.png)
![mh|600](https://chaotik.co.za/images/mechanics/movement-hexes.png)
###### Isometric
![Daimonin|500](https://upload.wikimedia.org/wikipedia/commons/e/ef/Daimonin_Stoneglow_beta4.png)
![address|500](https://d33wubrfki0l68.cloudfront.net/2641726acde04de5948183b3ad7e22dab198350a/f48c1/img/blog/isometry/1.jpg)
#### Maps 
The idea is a map where you select what "board" your character is active in. best example funnily enough are Mario maps that you use to select the actual level. A very advanced is [Moonring](https://store.steampowered.com/app/2373630/Moonring/) that has an overworld map then enter the levels. The idea is either a popup or a board you move around in to enter other boards
### Rules Referee 
The character sheet could set the math done for you. But, it might be more useful to put it in a single file outside the sheet. This is where all the functionality users want to have for their games to be controlled in.

This I haven't properly thought through yet due to how complex for a game system will be.
So for now the method will be to attempt to recreate a bunch of games in POW and build up this feature to be able to handle it.
### Misc. Tool addons
#### Background Music Player
It can be an mp3 player. If we have it stream from a service that will be more tricky with a lot of red tape.
#### Calculator
Just a normal calculator to use whenever
## Social Features
These features are to help set up communities and organize friends.
### Account Pages
A simple social page with a profile image, about, other misc. information the site tracks like achievements.

Users can set a schedule chart on what days they are available and set who is able to view it.
Maybe a system of trust levels that show additional information might be cool. Strictly for safety especially for some of the following features. 
### Creating Orbs
When you create an Orb you give it a name, a description, a banner and a color theme. You choose what rulebooks, asset libraries, and pre-built world settings(maps and statblocks). You can also run a module which has the content preset and ready. Then finally choose what server from your access list to run it on.
It also has a chat.
### World Permissions
First, this feature is to hide spoilers. But, it can also be used to delegate organizing the orb. The permission system should work pretty much how the role system works for discord.
### Approval system
You can set that any changes, like statblocks, will be sent to the role that approves them. If it gets rejected the change gets reverted.
## Server Hosting
The point is for users to be able to host it using what ever method they want. Either by hosting it on one person's device, using a physical server, or using an online server. It would be good to be a feature to have users who are not hosting save their own creations locally.

I knowledge on server hosting is limited. I own a server that uses unraid to host games like minecraft and Project Zomboid. Later I plan to learn the process of website hosting and at some point POWs "hostablility".

Either way the idea is a free pack of files to set up a server. All that should have to be set up is who has access to add worlds to them and who are the admins.

On the user side there will be a tab to add the server through its IP to the list of servers you have access to. The Admin can manage how many worlds there are, and how many have access to the server.
## Market and Community Page
### Copyright and Fair Use
Games don't have copyright to their rules but they do for the written content and art they have made for it.
For ttrpg it is mostly based on their user agreements.
Games that are friendly to users creating and selling secondary content for them are fair game. Either way the burden of fair use falls on to those that use POW not on POW itself.
### Content Pages
User, groups and studios can set up pages of content free or for sale and be able to customize it. when it comes to becoming a marketplace legal help is necessary. A program for independent user and groups would have to be set up for them to be aloud to sell on the site.
# Future Wishes
These are low-priority features. They are not worth diving into until we get user feedback on POW. Which is why these are just wishes.

**Better Sheet Editor (Engine):** Increasing the customizability to make more aesthetically pleasing Sheets.

**Overlay Editor (Engine):** There will be a lot of premade Overlays already. Letting user create their own might be cool.

**Advance Map tools for the Board Editor:** In a way I am thinking about how advanced minecraft maps get. For example, setting up triggers for events to spawn enemies or change tiles. But, it's too much to think about right now.

**Clubs (Social):** A pretty experimental idea, its basically a feature to start groups people can join. It's simple since they can just create a Discord server for their club. We don't have to handle their communication. There are benefits, like sharing paid content. It's like an actual club where you'd borrow someone's rulebook.
The experimental part is to location lock your club. It should allow only members from your country, state, county, or city. Or to an organization like a school/college/company. Don't know how verification would be handled but its just a cool thought.

**Sound Effects (Engine):** A trigger system that already has to be created for pop up might also be able to be used for sound effects.

**Action Visual Effects (Engine):** Having actions trigger visual effects could make things interesting. Foundry can do that, but it's out of budget.

**Voice Controller (Engine):** The idea is to have a voice call(kinda iffy because discord). The features that might make it worth it are:
- whispering: speaking to one or more players without the rest hearing it.
- voice effects: being able to plugin user created effects.
- speech to text

**Action History Log:** Works alongside the chat. Text to speech and speech to text. The point is to easy the communication between people who use text chat and only voice chat. It works well for accessibility. Another purpose is to create logs in screenplay format. They should show players' in-character text, voice, and actions.

**Random Content Generator (Engine):** Used to generate npcs and monsters. The best direction is to create a framework. It should let people build their own generators.

**The use of LMMs (Engine):** Large Language Models might make good conversational NPCs. But, who knows how useful they'll be, especially when running them locally. They can seem smart, but their true abilities are unknown.

**3d Board(Engine):** At first, this was high on the list. But, we can do a lot with 2D. It was a headache to keep the same features for 3D. So I will not unless there is interest from customers for it.
# Time line
## Phase 1: ***POW: System Builder*** _demo_
The ***POW: System Builder demo*** is for a single user. It has the *Object Editor*, *Sheet Editor*, *Wiki-like Notes*, and *Basic Rules Referee*. It is to get user feedback on the interfaces to create a system. Along with getting as many people to test it out as possible by making it free.
## Phase 2 ***POW: System Builder***
With the feedback from the demo, refine the editors.
This is when the hosting functionality and basic social features are made. 
The permission and approval system will be worked on in the final product. 
The *Board Editor* will not have customization functionality yet. There will only be the default Turn Board. 
Distribute this version for $5. It will build an email list with the promise that the $5 will be a discount on the final product.
## Phase 3 ***Crowed Funding***
Hopefully some attention was gained from the _System Builder_. This part of the plan depends on how popular it was. If it wasn't, it would be best to improve it first. We should use feedback to find ways to do better.

To work further on the project proper financial options need to be evaluated. Either way enough work so far is showable for promotional material. This is a marketing and community building phase.
I plan to also start creating content around TTRPG systems other then DND.

A crowdfunding campaign is easier said then done but it a great way to gauge community support. Along with stretch goals to hit the wish list of features in the "Future Wishes".
Many point of research is deciding the goals amounts.