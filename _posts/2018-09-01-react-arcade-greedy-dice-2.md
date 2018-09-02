---
layout: post
title:  "React Arcade | Greedy Dice Pt. 2"
date:   2018-09-01 14:26:30 -0400
categories: blog
---

## React Arcade
Grab your tokens, take your tickets... Welcome back to the React Arcade!
This a blog series is meant to `increase` our `knowledge` and `improve` our `implementation` of React by making games.  

This is **part 2** of a two-part tutorial. You can find **part 1**[ here](https://david-vanderhaar.github.io/blog/blog/2018/08/25/react-arcade-greedy-dice-1/).

In [part 1](https://david-vanderhaar.github.io/blog/blog/2018/08/25/react-arcade-greedy-dice-1/) we:
- took a bird's eye view of the how to play Greedy Dice
- discussed what you'll need for the project
- described our design through wire frames

In this final post we'll:
- code up the skeleton of our game, creating bare minimum components and handlers
- discuss my implementation of the game's functions
- discuss my implementation of styling
- deploy a build of the game to github
- discuss pain points and what we learned while making the game.

## Skeleton Code
Let's set up the bare bones of our game components and handlers one component at a time. Generate the project scaffolding with the create-react-app cli. To generate a project use this terminal command `$ create-react-app project-name`.

#### Additional Libraries
For styling we'll use Materialize. We'll bring it in with the cdn by placing this in the header of public/index.html
```
<!-- Compiled and minified CSS -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0-beta/css/materialize.min.css">
<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">


<!-- Compiled and minified JavaScript -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0-beta/js/materialize.min.js"></script>
```

#### Creating our Components
We can create our component files via the terminal  
`touch src/Nav.js src/Players.js src/GameBoard.js src/Die.js`

#### App
Now let's get going with our main App.js. This was automatically generated when we used the create-react-app cli. Replace everything in App.js with the following code.

First, we'll import the React Component class, our stylesheet, and our three custom components which we'll create later.
 ```
import React, { Component } from 'react';
import './App.css';
import Nav from './Nav';
import Players from './Players';
import GameBoard from './GameBoard';
```

Next, we'll define the default state we planned from [part 1](https://david-vanderhaar.github.io/blog/blog/2018/08/25/react-arcade-greedy-dice-1/) of this tutorial. We can simply define this object outside of our App component class. Then we instantiate our App component and set our initial state in the constructor function.
```
const DEFAULT_STATE = () => {
  return { // our default state
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
}

class App extends Component {
  constructor() {
    super();
    this.state = DEFAULT_STATE();
  }
```

Inside of our App component we will define our handler functions. We define each function as a way to organize our thoughts on how the state will be changed in our child components later on. These functions are simply meant to update the global state of our app so there is no logic included here.
```
  handleRollDice(gameBoard) {
    this.setState({
      gameBoard,
    })
  }

  handleLockDie(gameBoard, players) {
    this.setState({
      players,
      gameBoard
    })
  }

  handleEndTurn(gameBoard, players, turnId) {
    this.setState({
      gameBoard,
      players,
      turnId
    })
  }

  handleKeepScore(players) {
    this.setState({
      players,
    })
  }

  handleEndGame() {
    this.setState(DEFAULT_STATE())
  }
```

Our `render()` function is the visualiztion of our component. Since we are at the top level of our application this will be made of of our child components: Players, GameBoard, and Nav. It is to these pices that we will pass all of our handlers and relevant data.   
- Our Nav component doesn't need any data so we'll simply plop it down.
- Players needs all the data from the `players` attribute of our state object, as well as the turnId so that we can later visualize whose turn it is.
- Our GameBoard gets the most love because it is the main hub and change agent in our data structure. It will need to know about all of the data in our state object as well as access to our handler functions. Remember our handlers are responisble for updating the state of our application so the GameBoard will need to be able to trigger these when a player passes or rolls dice etc.

```
  render() {
    return (
      <div className="App">
        <Nav />
        <Players players={this.state.players} turnId={this.state.turnId}/>
        <GameBoard
          players={this.state.players}
          gameBoard={this.state.gameBoard}
          turnId={this.state.turnId}
          winScore={this.state.winScore}
          onRollDice={this.handleRollDice.bind(this)}
          onLockDie={this.handleLockDie.bind(this)}
          onEndTurn={this.handleEndTurn.bind(this)}
          onEndGame={this.handleEndGame.bind(this)}
          onKeepScore={this.handleKeepScore.bind(this)}
        />
      </div>
    );
  }
}

export default App;
```

#### Nav
Nav is the simplest component in this app. Again, we'll import the Component class from React and return a simple nav element in the render function. We will take adavntage of the Materialize styling library we imported earlier and use the `nav-wrapper` class along with `brand-logo` and `center`.
```
import React, { Component } from 'react';

class Nav extends Component {
  render() {
    return (
      <div className="Nav">
        <nav>
          <div className="nav-wrapper">
            <div className="brand-logo center">Greedy Dice</div>
          </div>
        </nav>
      </div>
    );
  }
}

export default Nav;
```

#### Players
Importing our Component class and the custom Die class that we'll make later.
```
import React, { Component } from 'react';
import Die from './Die';
```

This component's render method is made up of two main parts. The first section maps over the array of player objects we passed from our App.js. It uses this data and displays the player's id and score. Additionally, we use the turnId to determine if we should display our turn icon. You can use any icon you like for this.  
The `flow-text` class is used to dynamically change the font size of our player score. This is given to us by Materialize.
```
class Players extends Component {
  render() {

    let playerScores = this.props.players.map((player) => {
      return (
        <div key={player.id} className="col s6">
          <h3>
            Player {player.id}
            {
              (player.id === this.props.turnId) &&
                <i className="turn-icon material-icons amber-text">access_time</i>
            }
          </h3>
          <div className="flow-text">{player.score}</div>
        </div>
      )
    });

```

The second section of our render method will display the current player's dice pool. These are the dice the player has set aside while trying to score points.
First, we'll target the current player by filtering the player object out using the turnId.   


Next we'll map over the current player's locked dice and place a Die component inside of a div element marked with the `col` class. On large screens we can display the column at a width of 2 and on small screens we'll give it a width of 6.
```
    let currentPlayer = this.props.players.filter((player) => player.id === this.props.turnId)[0]
    let diceLocked = [...currentPlayer.diceLocked, ...currentPlayer.currentDiceLocked].map((die, i) => {
      return (
        <div key={die.id} className="col s6 m4 l2">
          <Die value={die.value} />
        </div>
      )
    });

    return (
      <div className="Players">
        <div className="row">
          {playerScores}
        </div>
        <div className="row locked-dice">
          {diceLocked}
        </div>
      </div>
    );
  }
}

export default Players;
```

#### Die
After importing our React Class, we'll return a div with a conditional className. it will always have the main class of `Die` and depending on the state of the Gameboard we may want to add the `rolled` class to the Die to visualize a die rolling along the table.  

The last thing we'll do is attach an onClick method to the die element so that we can trigger a state change when the player selects a die from the Gameboard.  
```
import React, { Component } from 'react';

class Die extends Component {
  render() {
    return (
      <div className={this.props.rolled ? 'Die rolled' : 'Die'} onClick={this.props.onClick}>
        {this.props.value}
      </div>
    );
  }
}

export default Die;
```

#### Gameboard
In our final component, we'll import our Die and a new library called uuid. You can install this and add it to your package.json with the following terminal command: `npm install uuid --save-dev`
```
import React, { Component } from 'react';
import Die from './Die';
import uuid from 'uuid';
```

The majority of this component will be writing functions to handle game logic and hooking those functions up to user input. This allows us to keep the render method relatively simple.   

Notice that most of these function end with a call to the handlers we defined in App.js accessed through the props we passed to the Gameboard component.
```
class GameBoard extends Component {

  rollDice() {
    let player = this.props.players.filter((player) => player.id === this.props.turnId)[0]
    let number = this.props.gameBoard.diceRolled.length === 0 && !player.hasRolledThisTurn ? 6 : this.props.gameBoard.diceRolled.length
    player.hasRolledThisTurn = true;
    let diceRolled = []
    while (diceRolled.length < number) {
      let value = Math.floor(Math.random() * 6) + 1; // get random value between 1 and 6
      let id = uuid();
      diceRolled.push({id: id, value: value});
    }

    let gameBoard = {...this.props.gameBoard}
    gameBoard.diceRolled = diceRolled;

    this.props.onRollDice(gameBoard);

    if (this.calculateScoreCombo(gameBoard.diceRolled) <= 0) {
      this.endTurn(false);
    }
  }

  lockDie(die) {
    let gameBoard = {...this.props.gameBoard}
    let players = this.props.players.concat()

    let player = players.filter((player) => player.id === this.props.turnId)[0]
    player.currentDiceLocked.push(die);

    let index = gameBoard.diceRolled.findIndex((d) => d.id === die.id);
    gameBoard.diceRolled.splice(index, 1);

    gameBoard.currentScore = this.calculateScoreCombo(player.currentDiceLocked)

    this.props.onLockDie(gameBoard, players);
  }

  endTurn(shouldKeepScore = true) {
    if (shouldKeepScore) { this.keepScore(); }
    let players = this.props.players.concat().map((player) => {
      player.diceLocked = [];
      player.currentDiceLocked = [];
      player.hasRolledThisTurn = false;
      return player
    });
    let gameBoard = {...this.props.gameBoard}
    gameBoard.diceRolled = [];
    gameBoard.currentScore = 0;
    let turnId = this.props.turnId === 1 ? 2 : 1;

    let player = this.props.players.filter((player) => player.id === this.props.turnId)[0]
    if (!this.checkForWin(player)) {
      this.props.onEndTurn(gameBoard, players, turnId);
      alert('next players turn')
    }
  }

    checkForWin(player) {
    if (player.score >= this.props.winScore) {
      alert('Player ' + player.id + ' Wins!');
      this.props.onEndGame();
      return true;
    } else {
      return false
    }
  }

  keepScore() {
    let players = this.props.players.concat();
    let player = players.filter((player) => player.id === this.props.turnId)[0]
    player.score += this.props.gameBoard.currentScore;
    player.diceLocked = [...player.diceLocked, ...player.currentDiceLocked];
    player.currentDiceLocked = [];
    this.props.onKeepScore(players);
  }

  // check 3 o kind
  calculateThreeKind(dice, value) {
    let kindAmount = dice.filter((die) => die.value === value).length;
    if (kindAmount >= 3) {
      let basePoints = value * 100;
      if (value === 1) {basePoints = 1000} // special case for tripple ones
      let amountOverThree = (kindAmount - 3)
      while (amountOverThree > 0) {
        basePoints = basePoints * 2;
        amountOverThree--;
      }
      dice = dice.filter((die) => {return die.value !== value})
      return basePoints;
    } else {
      return 0;
    }
  }

  checkForThreeKind(dice) {
    let threes = []
    for (let i = 1; i <= 6; i++) {
      threes.push(this.calculateThreeKind(dice, i));
    }
    return threes.reduce((acc, curr) => {
      return acc + curr;
    }, 0);
  }

  checkForSingles(dice) {
    return dice.map((die) => {
      if (die.value === 1) {return 100}
      else if (die.value === 5) {return 50}
      else { return 0 }
    }).reduce((acc, curr) => {
      return acc + curr;
    }, 0);
  }

  calculateScoreCombo(dice) {
    let result = [];
    result.push(this.checkForThreeKind(dice));
    result.push(this.checkForSingles(dice));
    return result.reduce((acc, curr) => {
      return acc + curr;
    });
  }
```

In the render method we'll visualize the dice that have been rolled, put in a couple of buttons so that players can act, and display the score that would be gained if the player ended their current turn.
```
  render() {
    let diceRolled = this.props.gameBoard.diceRolled.map((die, i) => {
      return (
        <Die key={die.id} value={die.value} rolled={true} onClick={() => {this.lockDie(die)}}/>
      );
    });

    return (
      <div className="GameBoard">
        <div className="actions">
          <div className="row flow-text">
            <h3>Current Score: {this.props.gameBoard.currentScore}</h3>
          </div>
          <div className="row">
            <button className="btn" onClick={() => {this.rollDice()}}>
              Roll
            </button>
            <button className="btn" onClick={() => {this.endTurn()}}>
              Keep Score & End
            </button>
          </div>
        </div>
        <div className="diceArea">
          {diceRolled}
        </div>
      </div>
    );
  }
}

export default GameBoard;

```

## Styles

Here is the CSS used to style the game. It is relatively minimal. Modify it to your heart's content!

```
body {
  background-color: #3F51B5;
  color: white;
}

.App {
  text-align: center;
}

.Nav .nav-wrapper {
  background-color: #303F9F;
}

.Players .locked-dice {
  background-color: #303F9F;
  margin: 10px;
  padding: 10px;
  border-radius: 10px;
}

.Players .turn-icon {
  padding-left: 20px;
}

.GameBoard .diceArea {
  border: 5px solid #303F9F;
  border-radius: 20px;
  margin: 10px;
  padding: 10px;
  min-height: 45vh;
}


.Die {
  height: 50px;
  width: 50px;
  display: inline-block;
  background-color: #C5CAE9;
  border: 2px solid black;
  border-radius: 5px;
  text-align: center;
  font-size: 30px;
  font-weight: bold;
  color: black;
  cursor: pointer;
  transition: .6s;
}

.Die:hover {
  box-shadow: 10px 10px 15px black;
  z-index: 2;
  transition: .6s;
}

.rolled {
  position: relative;
}

@keyframes spin { 100% { -webkit-transform: rotate(360deg); transform:rotate(360deg); } }

```

## Deployment
If you'd like to deploy this app so that others can play, we can do so for free with the `gh-pages` package. Find the simple guide [here](https://github.com/gitname/react-gh-pages).

## Wrapping Up
And this concludes our first entry to the React Arcade. If you have any ideas, questions or concerns. Contact me on twitter @classwook or email [d.vanderhaarhunter@gmail.com](d.vanderhaarhunter@gmail.com).

### Until Next Time

## Take it Easy
