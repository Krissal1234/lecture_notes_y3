what should you do when you have strategic interaction
- sometimes the best thing to do is counterinuitive

game theory is the study of how to mathematically determine the best strategy for given conditions in order to optimise the outcome 

Game theory studies the ways in which strategic interactions among rational players producce outcomes with respect to the players preferences

It helps people to decide if its a good idea to open a new store, to invest in a certain stock, if they should cut down their prices


look into Game theory in Fintech



nash equilibrium is the best move we can do
- The nash equilibrium tells you that if you play the nash equilibria infinitely many time then you should not lose
it is a pair of strategies (a*,b*) in a two player game such that a* is an optimal strategy for a* against b* and b* is an optimal strategy for B against a*

Not every game has a nash equilibrium. On the other hand some games have multiple

Bazeman auction
- Baseman proposed a auction of a 100 dollar bill
- the highest biddder would get the 100
- he added a twist, the person bidd second highest also had to pay is bid and get nothing
	- price went up to 465



Finding Nash equilibria is not always straight-forward
- recursive thinking is a problem in many games


The two games are often thought in game theory
- Guess 2/3 of the average
- Keynes Beauty contest game

formally what is a game?
- A game consist of the following elements
	- players - Who participates
	- strategies - what can each player do
	- payoff - the outcome of the game
	- knowledge - how does the game work

A strategy $s_j$ is a complete contingency plan that defines which actions player $j$ may take for all possible states of the game


What is a strategy?
A strategy is a course of action to a player. A game typically has many strategies

Payoffs are the final returns of the players at the conclusion of the game
payoffs are usually measured 


Nash Equilibrium
- A pair of strategies $(a^*,b^*)$ in a two player game such that $a^*$ is an optimal strategy for A against $b^*$ and $b^*$ is an optimal strategy for B against $a^*$
	- 

Rules
1. There are a finite number of players
2. the list of finite number of possible courses of action is available to each of the players
3. Each player ahs the knowledge of alternatives
4. Each player is associate d with an outcome
5. contiunuse...


Zero sum games - e.g. tic tac to


Normal form gamea

nash equilibrium is

nash equilibrium is hard it is NP Hard problem, especially in mixed problems

Applications of Game Theory

- business
- finance
- politics
- game playing
- market trading


there is no pure nash equilibrium to rock paper scisors


Banks dilemma
- We have fintech and we have the banks
- should the banks and new fintech startups cooperate or not
- At a theoretical viewpoint the nash equilibrium is to cooperate
	- it is because humans dont use mathematics but they use emotions


## [Counterfactual Regret Minimization – the core of Poker AI beating professional players](https://int8.io/counterfactual-regret-minimization-for-poker-ai/)




![[Pasted image 20240522154627.png]][[Pasted image 20240522154650.png]]


#### Simultaneous vs Sequential
- Simultaneous games are those in which players acct without knowledge of previous actions or outcomes. **All players make their moves at the same time**
- Sequential games are those in which players have some knowledge of previous actions
- **Perfect Information:** all players know the moves previously made by all other players up to the end of the game( e.g. chess )
![[Pasted image 20240522155147.png]]


assymmetric
- these games involve different strategy sets for each player
- each player has a unique set of options or roles in the game

zero sum games
the total gain and loss among players is zero. This means that one players gain is exactly balanced by the loss of another player

non zero sum
- games where total of gains and losses doe snot necessarily equal zero. in these games it is possible for all players to gain or fall all to lose
- this makes cooperation a viable strategy
- e.g. prisoners dilemma


![[Pasted image 20240522162512.png]]





### Dominant Strategies
When a player tries to choose the best strategy among a multitude of options, that player may compare two strategies A and B to see which one is better. The result of the comparison is one of:

B **is equivalent to A** - choosing B always gives the same outcome as choosing A, no matter what the other players do

B **strictly dominates** A - choosing B always gives a better outcome than choosing A, no matter what the other players do

B **weakly dominates** A - choosing B always gives at least as good an outcome as choosing A, no matter what the other players do, and there is at least one set of opponents actions for which B gives a better outcome than A

B and A are **intransitive** - B and A are not equivalent, and B neither dominates, nor is dominated by A. Choosing A is better in some cases, while choosing B is better in other cases, depending on exactly how the opponent chooses to play

B is **weakly dominated by** A - There is at least one set of opponent's actions for which B gives a worse outcome than A, while all other sets of opponents' actions give A the same payoff as B

B is **strictly dominated by** A - choosing B always gives worse outcome than choosing A, no matter what the other players do

##### We can now generalise
- Strategy B is **strictly dominant** if strategy B strictly dominates every other possible strategy
- Strategy B is **weakly dominant** if strategy B dominates all other strategy, but some strategies are only weakly dominated by B
- Strategy B is **strictly dominated** if some other strategy exists that strictly dominates B
- Strategy B is weakly dominated if some other strategy exists that weakly dominates B


Dominant strategy 
- a strategy is considered dominant when it is better than any other strategy for one player,  no matter how the opponents may play
- In the prisoners dilemma, each player has a dominant strategy 

### imp
looking at a payoff matrix, we deduce the dominant strategy by checking the outcomes if the other strategy was chosen **for the same player**. This is dominant strategy for a singular player, dont check the outcome of the other player
##### Dominant Strategy vs Nash equilibrium
A dominant strategy is a strategy which results in the best payoff for a player no matter what te other player does
A nash equilibrium represents a strategy which maximises payoff given what the other player would do - picture a third party figuring out the best strategy for both players

A nash equilibrium is conditional upon the other player's best strategy, but a dominant strategy is unconditional

we reach a nash equilibrium by assuming that the other player is rational, but we can follow a dominant strategy  without forecasting expected strategy of the opponent
a game can have a nash equilibrium even if there is not dominant strategy