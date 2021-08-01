# TravelingRobot's NAI Modules
Here I will collect my [custom modules](https://naidb.miraheze.org/wiki/Detailed_Concepts#AI_Modules) for [Novel AI](https://novelai.net/).

## TV Shows

### The One With The Friends Episodes
Trained on all episodes of the TV Show F.R.I.E.N.D.S.

#### Input convetions: 
* `⁂` to indicate the beginning of a new episode, `***` to indicate time lapse or new scene\
* `(Scene: <description>)` after `⁂` or to `***` specify the scene.
* 

**Steps used to train**: 3.000 (54%)\

## Generators

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
**Raw Corpus**: [yomomma-api](https://github.com/rdegges/yomomma-api/blob/master/jokes.txt)
