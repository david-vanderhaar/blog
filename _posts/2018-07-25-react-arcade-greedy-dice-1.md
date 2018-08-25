---
layout: post
title:  "React Arcade | Greedy Dice"
date:   2018-07-25 14:26:30 -0400
categories: blog
---

## React Arcade
Grab your tokens, take your tickets... Welcome to the React Arcade!
This is a blog series which I hope enjoys a long life. The idea is to `increase` our `knowledge` and `improve` our `implementation` of React by making games. In [a previous blog post](https://david-vanderhaar.github.io/blog/blog/2018/02/25/react-is-easy/) I discuss the value of game development as a learning tool for web development. I believe this is especially true for component based, reactive frameworks.

Each post will follow a similar format where we'll:
- take a bird's eye view of the game we're making
- discuss what you'll need for the project
- describe our design through wire frames
- code up the skeleton of our game, creating bare minimum components and handlers
- discuss my implementation of the game's functions
- discuss my implementation of styling
- deploy a build of the game to github
- discuss pain points and what we learned while making the game.

Without further ado let's get started with our first entry for the `React Arcade`!

## Today's Game
In this post we'll be creating a digital game of dice for two players called Greed. This is a push-your-luck game where each player rolls to be the first to gain some high score. Here's an [in-depth description](http://janbroussard.com/Greedy.html).
### Details
- Our game will use of six dice.
- Each turn a player may roll and keep dice OR end their turn with the points accumulated that turn.
- If a player rolls and does not have a scoring combination of dice, the points are lost and the next player takes her turn.

## What You'll Need
1. install create-react-app on your system and glance at the [docs](https://github.com/facebook/create-react-app) for a quick understanding of how to use it.
1. A medium for creating wire frames. I use pen and paper, but feel free to use software such as [Wireframe.cc](https://wireframe.cc/)

## Wire Frames
#### Describing our design through wire frames

The design of this game is simple enough that I only needed one wire frame to adequately plan my approach.

![Greedy Dice wire frames](/blog/assets/images/greedy-dice-frame.jpg "Greedy Dice wire frames")

You'll notice that my plan for this game is broken into four components: navbar, players' data, gameboard, and die. Next, I will plan out the functionality of each component. Each component will have two types of jobs; displaying data, and/or handling data. This is illustrated in the image below.

![Greedy Dice wire frames](/blog/assets/images/greedy-dice-functions.jpg "Greedy Dice wire frames")

**Navbar**  
This is the simplest component. Its only job is to `display` the game's title.

**Players**
This component is also fairly simple in function. It will be responsible for:
- `displaying` the current player,
- `displaying` the current player's set-aside dice, and
- `displaying` each players' overall score.

**GameBoard**
This component will house the meat of our game logic and functionality. It will:
- `display` the current score based on the dice set-aside
- `display` the dice rolled
- `handle` rolling new dice
- `handle` ending a player's turn
- `handle` setting dice aside for scoring
- `handle` detecting when the player loses their turn

**Die**
This represents a single die and is only responsible for `displaying` the dice within our **Players** and **Gameboarb** component.

The last thing we should define before starting is our app's state tree. This will allow us to easily see which component will need what data. It will allow us to better remember where data needs to be passed and how it will be manipulated. Here is a sketch of our default state. You can think of this as our starting data.

Our game will begin with some bare bones data:
- an array holding two player objects, each of which will have
  - an id,
  - an overall score,
  - a current turn score (which can be lost on a bad roll),
  - an array holding the dice locked during the current turn,
  - an array holding dice locked during current roll,
  - a boolean telling whether or not the player rolled this turn yet.
- a gameboard object that has
  - an array holding the dice rolled
  - an array holding the dice locked by the current player
  - current score based on dice rolled
- a turn id number, saying which player is rolling
- a score at which the players will achieve victory

```
{ // our default state
  players: [
    {
      id: 1,
      score: 0,
      scoreThisTurn: 0,
      diceLocked: [],
      currentDiceLocked: [],
      hasRolledThisTurn: false,
    },
    {
      id: 2,
      score: 0,
      scoreThisTurn: 0,
      diceLocked: [],
      currentDiceLocked: [],
      hasRolledThisTurn: false,
    },
  ],
  gameBoard: {
    diceRolled: [],
    diceLocked: [],
    currentScore: 0, //based on all dice selected
  },
  turnId: 1,
  winScore: 5000,
}
```
At this point we have enough of a plan to begin coding our components. In the next post we'll see my implementation of this plan. As a challenge, try and implement the functionality yourself. You may use [my finished version of Greedy Dice](https://github.com/david-vanderhaar/react-arcade-greedy-dice) as a reference.

### Until Next Time

## Take it Easy
