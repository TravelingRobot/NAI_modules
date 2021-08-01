# TravelingRobot's NAI Modules
Here I will collect my [custom modules](https://naidb.miraheze.org/wiki/Detailed_Concepts#AI_Modules) for [Novel AI](https://novelai.net/).

## TV Shows

### The One With The Friends Episodes
Trained on all episodes of the TV Show F.R.I.E.N.D.S.

It is not producing great results right now. Output is quite incoherent, and Sigurd keeps confusing the characters. Maybe it could be improved by Lorebook entries?

#### Input conventions: 
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
