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
```
R = 0r + (-1)p + 1s

P = 1r + 0p + (-1)s

S = (-1)r + 1p + 0s
```

Using basic simplification methods we obtain:

```
R = s - p

P = r - s

S = p - r
```

Since this is a zero-sum game, we can assume that the total payoff, regardless of the matchup that takes place the place, will be of 0. Therefore, we can assume that `R = P = S = 0`

And the fact that our opponent must select throw, we can also make the assumption that 
`r + p + s = 1`

With all these simple equations we can solve:

```
R = 0 = s - p -> p = s
```
We apply the exact same procedure for the last 2 equations and we get the following:

```
r + p + s = r + r + r = 1
3r = 1 
r = 1/3
```

Since r + p + s = 1, **p = 1/3** and **s = 1/3**

Theoretically speaking, these results shows us that the pick rate of how often an action is taken is equal across all choices. But in the end of the day, humans would try to play randomly but they will inebitably fall under certain patterns and if you manage to pick up the habits that a certain player has, you can exploit it in order to win more games by countering their choice that is most likely to be taken.

**Note:** This is just the extensive analysis of a zero-sum game. In the next section we will be using the formulas we got from here and we will try to apply it to any RTS game in order to balance it.

### Applying zero-sum games to RTS

Now we will create our own theoretical RTS game where we have 3 units: A, B, and C. A counter B, B counters C and C counters A. 
For the calculations, instead of using ratios, we will now use a term widely used in RTS, and that's the resources units cost. 

|-|Cost| % of health lost|
|---|---|---|
| **A**| 50 | 0 | 
| **B**| 100| 20% |
| **C**| 150 | 40%|


## Resource systems, management and control of its economy

The dawn of resource systems can be tracked back in the 1990s where Dune 2 had a single collectable resource that was melange (or spice) that was gathered from sand and could be sold at certain locations for credits. And credits were used to upgrade units and structures.

The system were a worker (or harvester) has to manually go to the location of the resource, collect it and bring it back to the main base was also developed in this game. 

Since this pioneering design, different games have experimented different types of resources at the same time, its collection or gathering and the rate of expense of said resources.

### Rate of expense

- **Continuous:** When spending any resource on something, the credit count is **continuosly** substracted from the player's bank until the purchase/upgrade is complete. This means that you can actually buy something that you initially don't have enough credits to buy. It can also be possible that you make multiple purchases and none of them will be completed. This system plays heavily with the income per second of the player.

- **Discrete:** When making making any kind of transaction, the credits are substracted **immediately** from the player's bank. This means that the player cannot make a purchase they cannot afford at that exact moment. This really simnplifies the economy that the players has to manage and allows the players to focus more on other important aspects of the games, such as the state of the macro or in base-building.

**Note:** Essentially, both systems would yield the same exact amount of resources (assuming that the gathering rate is the exact same). However, the decision making widly varies between these two systems. The first one you could actually begin to build something ahead of time in order to cut off in building time. The second one is way more intuitive as anyone knows if they have enough credits to make a purchase. And in the case they don't, usually the game itself will alert the player that his action cannot be taken.

### Types of gathering

- **Active:** This usually requires 3 game entities in order to start producing income. One is the storage, the other one the worker and the last one is the resource field. This often means that there are limitations in the amount of resources available for each player. They will have to fight in order to establish control and be able to outgrowth the enemy in terms of economy.

- **Passive:** The only entity needed is the one that would be extracting/gathering the resurce. This simplifies the gathering a lot as the onlything the players has to do is to defend his collectors and try to sabotage or destroy the oponents'. Usually, the amount of resource is infinite and it's not bound to the abundance that the maps has.

### Control of economy and player agency

In this section, we will analyze how the control of the game's economy (its resources) affects how the player can influence the game's state. 

In RTS, one of the quintessential aspects is having an economic systems of some sort so that players must have a deep understanding of said system in order to find any possible exploits in order to leverage the advantage to their side. The absolute core of an RTS is not having hordes of units having a massive battle, but it's closely related to the adquisition and expenditure of what we will call **value.** Value is the pure definition for resources, not just the resource that any game uses per se, such as minerals and gas StarCraft but anything that you can purchase, trade or upgrade with it.  

This is where player agency comes to play. The definition for this concept can be summarized as "the ability of any player to interact and change the game's state throughout the course of the match.

So why this aspect of RTS is the root of almost all games in this genre? The key word is progress. This system allows to put pressure on the players the moment a match begins for a race on who is the one that can collect resources more efficiently and spend it in the best possible way taking into consideration how his enemy plays. This is closely related to the overall state of the economy for both players. Progress is often represented with physical objects that both users can interact with (units, structures or upgrades). The player has to intentionally invest his income in order to progress through the match by building, fighting and upgrading his base and army. 

This means that both players have the agency to **directly** interfere with his enemies' economy at any point of the game by sending troops to sabotage or preferably to destroy his collectors or kill his harvesters. This means that players **ought to lose** invested value in the form of buildings/troops. The more proactive and thoughtful actions that one players takes, the more overall agency he will possess. This means that he will have a wider array of options to influence the state of the game compared to his opponent, who fell

## Artificial Intelligence (AI)

AI must fit the game's intended experience. Good AI is not only the one who can beat the player. 

The complexity of the AI within any game is 

### Make machine driven units more resilient

ty making enemy units that the game itself controls, it makes the player thing that they are more intelligent that they actually are. This sensation is achieved because he feels challegend when facing tougher enemies, therefore, he needs to build and think strategies that can work againts units that have more HP and damage. The process of making the player come up with a strategy indirectly makes him think that the AI is harder to deal with.

### Make the AI have different personalities

You should make every encounter and battle feel unique in a way that can be memorable for the player. Maybe one opponent can have a build order optimized in getting map control early in the game so they establish a superior economy than the player, so they would be ovwerwhelmed by a huge army. Perhaps another can have a build order that's suited for fast-paced games where the AI rushes the players base early on and tries to win via early and successful skirmishes.

A great example of this concept is portayed in the game Civilization's single player modes, where the leaders all have their own uniqueness, therefore, you have to develop a strategy for that single leader. And probably the same strategy won't work against another foe.

### AI needs to be predictable

Halo's Tech Lead, Chris Butcher said: 
> "*The goal is not to create something that is unpredictable. wha you want is AI that is consistent so that the player can give certain inputs. The player can do things and expect the AI will react in a certain way.*"

This allows to play the game with **intentionality.** This is defined by Far-Cry's 2 designer as the following:

> "*The ability of the player to divise his own meaningful goals through his understanding of the game dynamics.*"

By making AI predictable, it encourages the player to develop and ideate plans that when executed successfully, is satisfying to observe the results. It wouldn't be the same if the same plan only worked half of the time. 

### AI should be able to interact with the game's systems

This is crucial when making an AI seem like it's alive and smart. This makes the player feel like the machine has the same choices. This behaviour can also be exploited by the player if he ever perceives a pattern in its behaviour. 

In RTS games, this could be done by making the AI gather and manage resources in order to develop his own strategy (even if the machine has a higher income to make it harder to play against), instead of granting them for free and make them unlimited for the AI. Thus, making it nearly impossible for the player to deal with.

### Make the AI react to player's actions

If the machine notices that the player is focusing on getting a superior map control, they AI should fight for control too. You have to make that the AI is constantly trying to sabotage and get and edge over the player. It shouldn't blindly follow a programmed build order and stick to it no matter what. This are the instances where the machine feels like a machine. And we should always try to avoid that.

This is also crucial to make every encounter feel unique. Because it prevents the player from just setting up a specific build order and beating every campaign with the same boring, unchanging strategy.

### Good AI for friendlies!

This is not intended to be applied to RTS because rarely, if not never, you won't be working alongside an AI-driven ally. But it's a nice way to add more value and meaning to the game. 

An extremely good example analysing Final Fantasy XV's character, Prompto, who will be taking selfies when certain thresholds have been triggered or when the character feels like doing so. Gameplay wise, this has no value whatsoever. But it adds a tremendous amount of complexity to Prompto's character and makes him feel like he's self-aware.






## Bibliography and Webgraphy 

### Links

#### Balancing
- **Game balance:** https://en.wikipedia.org/wiki/Game_balance

- **Introduction to unit balancing:** http://www.oxeyegames.com/rts-game-play-part-5-introduction-to-unit-balancing/

- **Intransitive mechanics:** https://gamebalanceconcepts.wordpress.com/2010/09/01/level-9-intransitive-mechanics/

- **Pay-off table definition:** http://kfknowledgebank.kaplan.co.uk/KFKB/Wiki%20Pages/Payoff%20tables.aspx

#### Resource/economy management 

- **Resource systems:** http://www.oxeyegames.com/rts-game-play-part-2-resource-systems/

- **Resource management in RTS:** https://waywardstrategy.com/2014/12/18/random-thoughts-on-resource-management-in-rts/

- **Control of the economic processes:** https://waywardstrategy.com/2015/11/23/rts-design-thought-control-of-economic-processes/



### Abstracts/PDFs

- ***Really extensive* article about Balancing Real-Time Strategy Games:** https://brage.bibsys.no/xmlui/bitstream/handle/11250/2463289/13662_FULLTEXT.pdf?sequence=1&isAllowed=y

- **Call for AI Research in RTS Games:** https://skatgame.net/mburo/ps/RTS-AAAI04.pdf)



### Videography
- **Perfect Imbalance by ExtraCredits:** https://www.youtube.com/watch?v=e31OSVZF77w

- **What Makes Good AI? by Game Maker's Toolkit:** https://youtu.be/9bbhJi0NBkk



