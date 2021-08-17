# TravelingRobot's NAI Modules
Here I will collect my [custom modules](https://naidb.miraheze.org/wiki/Detailed_Concepts#AI_Modules) for [Novel AI](https://novelai.net/).

## TV Shows

### The One With The Friends Episodes
Trained on all episodes of the TV Show F.R.I.E.N.D.S.

It is not producing great results right now. Output is quite incoherent, and Sigurd keeps confusing the characters. Maybe it could be improved by Lorebook entries?

#### Input Conventions
* `⁂` to indicate the beginning of a new episode, `***` to indicate time lapse or new scene\
* `(Scene: <description>)` after `⁂` or to `***` specify the scene.
* `<Name>: <Dialogue>` dialogue is entered *without* `"`
* `(<event>)` or `(<action>)` can be enterd between dialogue or on its own line

```
(Scene: Monica and Chandler's, Ross is there with Rachel.)
Ross: Hey! Where you been? I've been trying to get a hold of you. How are ya?
Rach: Oh good. You know me, always busy. What have we got here? A little something for the office party?
Ross: Yeah, yeah it was just an idea that popped into my head. (He hands her a wrapped box) Well what do ya think?
Rachel: Wow! It's beautiful! Thank you so much!
(Chandler and Monica enter)
Chandler: Hi guys!
Monica: Hey, hey! We're not interrupting anything am I right?
Ross: No no no! Not at all! Come on in!
```

**Module Download**: [link](https://github.com/TravellingRobot/NAI_modules/blob/main/tv_shows/friends/F.R.I.E.N.D.S..module)\
**Steps used to train**: 3.000 (54%)\
**Cleaned Corpus**: [link](https://github.com/TravellingRobot/NAI_modules/blob/main/tv_shows/friends/Friends_Transcript_cleaned.txt)\
**Raw Corpus**: [Friends TV Show Script by Divyansh Agrawal](https://www.kaggle.com/divyansh22/friends-tv-show-script)

## Generators

### Forbidden Lands Random Encounters
A module trained on material from [Forbidden Lands](https://freeleaguepublishing.com/en/games/forbidden-lands/), an Swedish open world dark fantasy RPG. Trained on the 42 random encounter from the gamemaster's guide.

It can sometimes generate some interesting ideas, but will need some rerolling and editing to generate something useful. Tends to break down after it generated the first encounter, so it is recommended to start over anew for each encounter.

Turn bracket generation **off**!

Start the Prompt with
```
***
[ Tags:
```

#### Input conventions
* `***` indicates the beginning of a new encounter
* `[ Tags: <tags> ]` can be used to indicate the type of the encounter. Does not always work reliably, however. See next section for tags used in the training data, but other tags might work as well.
* `[ Terrain: <terrain types> ]`  can be used to indicate the type of the terrain this encounter can take place in. Encounters used in the training data were: `Plains`, `Forest`, `Dark Forest`, `Hills`, `Mountains`, `Lake`, `Marshlands`, `Quagmire`, `Ruins`.
* `DECSRIPTION:` marks the beginning of the Read-Aloud text of the encounter
* `GM NOTES:` marks the beginning of the background info for the GM

#### Tags used in the training data
* `Characters` for encounters that contained NPCs, usually in combination with additional keywords specifying the type(s) of NPCs. Possible subcategories: `Humans`. `Elves`, `Dwarves`, `Orcs`, `Halflings`, `Goblins`, `Trolls`, `Ogres`, `Saurians`, `Rust Brothers`, `Slavers`, `Merchant`, `Belderan Clan`
* `Monsters` for encounters that contained monsters, usually in combination with additional keywords specifying the type(s) of monster. Possible subcategories: `Ents`, `Minotaur`, `Giant Squid`, `Demons`, `Blood Mist`, `Gryphon`, `Abomination`, `Harpy`, `Undead`, `Death Knight`, `Ghost`, `Zombies`
* `Animals` for encounters that contained some kind of animal(s)
* `Landscape` for encounters that contained some special landmark. Possible subcategories: `Ruins`, `Tomb`, `Cottage`
* `Danger` for encounters that contained some sort of hazard. Possible subcategory: `Fire`
* `Friendly` for encounters that are unlikely to result in confrontation
* `Neutral` for encounters that *could* end in confrontation depending on PC behaviour, but have options to avoid it.
* `Hostile` for encounters that almost certainly will end in confrontation.
* other minor keywords were: `Alderlander`, `Corpse`, `Treasure`, `Ambush`, `Lure`

```
***
[ Tags: Characters, Humans, Neutral ]
[ Terrain: Hills and Mountains ]
DESCRIPTION: The wind howls through the forest. You hear a crackling noise in front of you. It's the sound of branches breaking underfoot as someone or something approaches from behind. Your heart beats faster. There are three figures standing on top of a hill. One is tall with long black hair, another one has short blond hair and wears dark clothes, while the third one seems to be wearing armor that covers him completely. All have axes at their hips. They stare down at you. "We're looking for some humans," says the man with the blond hair. "You might know where they've gone?" he asks.
GM NOTES: The three men are called Harker, Karsk and Sveta. They want to find some humans who disappeared into the woods near here several days ago. If the adventurers agree to help them out, they will tell them about the village of Ljoten which lies up ahead. The villagers were attacked by bandits led by two orcs, but managed to drive off the attackers. However, the bandits captured many people including children, women and old men and took them back to their hideout in the mountains. A search party went after them but never returned. Now the three men need your help if they are going to rescue these victims. The men may also provide information about other villages nearby.
```
**Module Download**: [link](https://raw.githubusercontent.com/TravelingRobot/NAI_modules/main/generators/fb_random_encounters/TR_%20Forbidden%20Lands%20Encounters_500.module)\
**Steps used to train**: 500 (976%). Other modules with 250, 1k and 2k steps were also trained for experimentation (available [here](https://github.com/TravelingRobot/NAI_modules/tree/main/generators/fb_random_encounters/alternative_step_amounts)), but 500 steps yielded the best results.\
**Cleaned Corpus**: Contains copyrighted material, contact me on discord for questions about the training data (*TravelingRobot#4142*).\
**Raw Corpus**: [FB Gamemaster's Guide](https://freeleaguepublishing.com/en/store/?product_id=4608913440905)

### Twilight 2k Encounter generator
**Many thanks to Orion for giving the idea for this module and donating the steps for it!**
A module trained on material from [Twilight 2k 4th Edition (kickstarter pre-release copy)](https://freeleaguepublishing.com/en/games/twilight-2000/), a post-apocalyptic military tabletop role-playing game from Free League Publishing. Trained on the 52 random encounter from the referee's guide. Uses the tagging from the referee's guide, but can sometimes interpret deviating tags in creative ways. See input convetions below for more details.

It can sometimes generate some interesting ideas, but as most generators it will need some rerolling and editing to generate something useful. Tends to break down after it generated the first encounter, so it is recommended to start over anew for each encounter.

Turn bracket generation **off**!

You can start the prompt with
```
***
```

#### Input conventions
* `***` indicates the beginning of a new encounter
* `[ Terrain: : <terrain type> ]` corresponds to the "On-Road and Off-Road" symbols from the referee's manual. This can be used to indicate the type of terrain for the encounter. In the training data, only the following tags were used: `On-Road`, `Off-Road`, `On-Road or Off-Road`. But NAI will come up with its own terrain types and interpret other terrain types as the ones used.
* `[ Time: <Time of Day> ]` corresponds to the "Night and Day" symbols from the referee's manual. In the training data this was simply used to indicate whether the encounter takes place during day- or nighttime. Seems to not have much of an impact on generation though. Tags used in the training data: `Day`, `Night`, `Day or Night`.
* `[ Situation: <type of situation> ]` corresponds to the "Night and Day" symbols from the referee's manual. in the training data this was simply used to indicate whether the encounter takes while the PCs are on the move or are staying in one place. Tags used in the training data: `Traveling`, `Camping`, `Camping or Traveling`.
* `[ Category: <type of category> ]` corresponds to the "stationary" symbol from the referee's manual. Use this to indicate the general type of encounter. Categories in training data: `Weather`, `Animal`, `Derelict Vehicle`, `Crater`, `Ruins`, `Refugees`, `Hunters`, `Marauders`, `Stragglers`, `Military Patrol`, `Military  Outpost`, `Military Convoy`, `Settlement`.
* `[ Theme: <theme> ]` corresponds to the 4 "motivations" from the referee's manual. Use this to indicate the general mood and theme of encounter. Themes in training data: `Violence`, `Wealth`, `Fellowship`, `Power`.
* `[ Faction: <factions> ]` corresponds to the FACTION bullet point from the referee's manual. Use this to indicate factions encountered. Factions in training data: `NA` (no characters present), `None` (NPCs are present but do not belong to clear faction), `Civilian`, `Marauder`, `Soviet Military`, `US Military`.
* `[ Number: <number(s)> ]` corresponds to the NUMBER bullet point from the referee's manual. Use this to indicate the number of NPCs encountered. Included in the training data out of curiousity, but do not expect too  much utility from this.

#### Structure of training data
The encounters in the training data were structured in the following way:

```
***
[ Terrain: Off-Road; Time: Day; Situation: Camping or Traveling ]
[ Category: Weather; Theme: Violence ]
[ Faction: NA; Number: NA ]
Here is a description of the encounter...
```

Encounters generated with only `***` will often only produce the first line of traits and then a description of the event. However, feel free to experiment with giving your own keywords and see what NAI does with it.

Prompt:
```
***
[ Theme: Fellowship
```

Output:
```
***
[ Theme: Fellowship ]
The PCs find a small outpost of the US Army. The soldiers are friendly, but they have no weapons and very little ammunition left for their rifles (only one bullet per soldier). They offer to let the PCs stay in return for some food or help with hunting down marauding wolves that threaten their livestock. If any PC is wounded during this encounter, it will be healed by an American doctor if he can get him there quickly enough. In addition, the Americans may provide them with information on local military units – such as which ones were stationed here before being withdrawn from the region, what kind of equipment was used and so forth.
***
[ Terrain: On-Road Craters ]
A short distance away from the road leading out of town, several large craters dot the ground. These craters look like long pockmarks on the landscape, made when a tank fired its main gun at point blank range into the earth's surface. The damage done by these shells has been absorbed over time by the soil and turned into small depressions filled with water.
```

**Module Download**: [link](https://github.com/TravelingRobot/NAI_modules/raw/main/generators/twilight_2k_encounter/TR_Twilight__2000_Encounters.module)\
**Steps used to train**: 500 (1386%). Another module with 350 steps were also trained with steps contributed by Orion for experimentation (available [here](https://github.com/TravelingRobot/NAI_modules/tree/main/generators/twilight_2k_encounter/alternative_step_amounts)). No obvious differences in results were observed between the 2 modules, but for now 500 steps is recommended.\
**Cleaned Corpus**: Contains copyrighted material, contact me on discord for questions about the training data (*TravelingRobot#4142*).\
**Raw Corpus**: [Twilight 2k Referee's Guide (kickstarter pre-release copy)](https://freeleaguepublishing.com/en/games/twilight-2000/)

### Yo Mama!
A module trained on 1040 Yo Mama jokes. Start your prompt with `Yo`.
```
Yo mama is so fat, she could be the Michelin Man.
Yo mama is so fat, you can put her in a car and drive to work!
Yo momma's so fat, when I saw her on TV, I thought it was Oprah Winfrey!
Yo mother-in-law's so fat, she looks like a cow with three legs!
Yo sister is so ugly, if she got hit by lightning twice, there'd still be sparks coming out of her ass!
```
**Module Download**: [link](https://raw.githubusercontent.com/TravellingRobot/NAI_modules/main/generators/yo_mama/Yo%20Mama!.module)\
**Steps used to train**: 90 (100%) Other modules with 50, 200 and 500 steps were also trained for experimentation (available [here](https://github.com/TravelingRobot/NAI_modules/tree/main/generators/yo_mama/alternative_step_amounts)), but 90 steps yielded the best results - don't worry the result is still awful...\
**Cleaned Corpus**: [link](https://github.com/TravellingRobot/NAI_modules/blob/main/generators/yo_mama/jokes_cleaned.txt)\
**Raw Corpus**: [yomomma-api by Randall Degges](https://github.com/rdegges/yomomma-api/blob/master/jokes.txt)
