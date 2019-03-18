# RTS Balancing

I am [Victor Chen](https://www.linkedin.com/in/victor-chen-556670182), student of the [Bachelor’s Degree in Video Games by UPC at CITM](https://www.citm.upc.edu/ing/estudis/graus-videojocs). This content is generated for the second year’s subject Project 2, under supervision of lecturer [Ricard Pillosu](https://es.linkedin.com/in/ricardpillosu).


# Introduction

In this project, I will be covering the basic concepts of balancing an RTS game and taking a deep dive in the complexity that they inherently carry. Furthermore, I will explain some of the methods used in order to reach our desired objective.

## Game Balance

First of all, in game design, the concept of balance is closely related to adjusting the rules and fine-tuning the stats for different game elements in order to avoid the abuse of one really strong mechanic/unit. Contrarily, you also don't want an ineffective or useless element that no one desires to use because of the fact that said element is overshadowed by everything else.

In RTS, balancing is a core aspect of the design of these specific genre. This is because a slight overtune on a stat on a specific troop can make the game revolve around creating and swarming with said troop. Thus making the game stale and one-dimensional rather than one relying on wits and outmaneuvering your opponent with a superior strategy.

## Unit balancing

Arguably one of the most important aspects of an RTS are the interactions between units in the battlefield to make the game feel like the strategies they've developed during the match have paid off.   
In RTS games, the player has a wide array of possible options when it comes to troop creation. Said troops **must** have a strength. This means that the unit must be better than other ones at doing a specific task or job. Nevertheless, they also **must** have some kind of inherent weakness that the other player facing that unit can exploit. And, more often than not, the mix of weaknesses of the units it's what makes the game truly fun, and that's what we are aiming to create.

### Zero-sum games
First and foremost, I will explain the most basic and traditional way of balancing elements, not just in video games but it can be used in board games or any game in general. And that's achieved by applying the essential theory of a zero-sum game. This theory explains that no matter what choices or decisions both players take, the sum of the outcome between positive or negative results **is always equal to 0**.  
Therefore, this means that there is no "best strategy" because of the fact that one choice can be countered by something else.

To exemplify this concept, I will use the prime example of a zero-sum game, Rock-Paper-Scissors. I will use a [pay-off table](http://kfknowledgebank.kaplan.co.uk/KFKB/Wiki%20Pages/Payoff%20tables.aspx) to better visualize all the possible outcomes. Keep in mind that we will be going back to this concept and using it as the research progresses.

R-P-S represents the choices we have.

r-p-s represents the choices the enemy has.

|-|r|p|s|
|---|---|---|---|
| **R**| 0 | -1 | +1|
| **P**| +1| 0  |-1 |
| **S**|-1 | +1| 0|

Let's convert these numbers into the ratio of one player chosing one option vs the others. Theoretically speaking, the ideal ratio would be 1:1:1 since there's no throw that's used more often than the others and no choice grants you a higher win percentage.

Taking into account the results provided by the table, we can extract the following formulas that will help us determine the payoff for each choice:

`R = 0r + (-1)p + 1s`

`P = 1r + 0p + (-1)s`

`S = (-1)r + 1p + 0s`

Using simple simplification methods we obtain:

`R = s - p`

`P = r - s`

`S = p - r`











# Bibliography 
[Game balance](https://en.wikipedia.org/wiki/Game_balance)

[Introduction to unit balancing](http://www.oxeyegames.com/rts-game-play-part-5-introduction-to-unit-balancing/)

[Intransitive mechanics](https://gamebalanceconcepts.wordpress.com/2010/09/01/level-9-intransitive-mechanics/)

[Pay-off table definition](http://kfknowledgebank.kaplan.co.uk/KFKB/Wiki%20Pages/Payoff%20tables.aspx)

## Video
[Perfect Imbalance by ExtraCredits](https://www.youtube.com/watch?v=e31OSVZF77w)



