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
**Steps used to train**: 500 (976%). Other modules with 250, 1k and 2k steps were also trained for experimentation (available [here](https://github.com/TravelingRobot/NAI_modules/tree/main/generators/fb_random_encounters/alternative_step_amounts), but 500 steps yielded the best results.)\
**Cleaned Corpus**: Contains copyrighted material, contact me on discord for questions about the training data (*TravelingRobot#4142*).\
**Raw Corpus**: [FB Gamemaster's Guide](https://freeleaguepublishing.com/en/store/?product_id=4608913440905)

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
**Steps used to train**: 90 (100%)\
**Cleaned Corpus**: [link](https://github.com/TravellingRobot/NAI_modules/blob/main/generators/yo_mama/jokes_cleaned.txt)\
**Raw Corpus**: [yomomma-api by Randall Degges](https://github.com/rdegges/yomomma-api/blob/master/jokes.txt)
