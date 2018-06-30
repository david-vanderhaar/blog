---
layout: post
title:  "React Arcade"
date:   2018-06-22 14:26:30 -0400
categories: blog
---

## React Arcade
Grab your tokens, take your tickets... Welcome to the React Arcade!

- game dev quote
- intro: what is this series, why this series (refer to game dev post)
- setting up react w/ create-react-app
- the game and its rules
- our approach (lite wire-frames)
- the main code
- styling

Steps:
1. In the terminal `create-react-app name-of-app`
2. for styling I'll use Materialize. We'll bring it in with the cdn by placing this in the header of public/index.html
```
<!-- Compiled and minified CSS -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0-beta/css/materialize.min.css">
<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">


<!-- Compiled and minified JavaScript -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0-beta/js/materialize.min.js"></script>
```
2. in App.js delete everything in between 'App' <div>, we'll be starting from scratch
3. create our component files `touch src/Nav.js src/Players.js src/GameBoard.js src/Die.js`
4. in App.js we'll define the overall state of our app by setting the default state in our components constructor function
5. let's go ahead and fill out what our App will render. Ultimately it will render three of our components, Nav, Players, and GameBoard. To use them here, we'll need to import them at the top of our file.
6. let's define each of a component files to a bare minimu so that we can run our app.
import React, { Component } from 'react';
```
class Nav extends Component {
  render() {
    return (
      <div className="Nav">
        Nav
      </div>
    );
  }
}

export default Nav;
```
7. test that your app renders by running `npm start` in the terminal
8. since we're using Materialize styles, the Nav component is cake! Heres what it looks like but feel free to customize it. This wouldn't be a bad time to explore [Materialize](https://materializecss.com/about.html) for yourself.
9. Now the players component. It consists of the players scores and the dice they have locked in place so in App.js well pass in state.players as a prop for use in the Players component



## Learn More About it
Here a few great articles on the subject.

1. [5 Questions Every Unit Test Must Answer](https://medium.com/javascript-scene/what-every-unit-test-needs-f6cd34d9836d)
2. [Guideline For Test Driven Development](https://msdn.microsoft.com/en-us/library/aa730844(v=vs.80))
3. [9 Benefits of Test Driven Development](https://www.madetech.com/blog/9-benefits-of-test-driven-development)

### Until Next Time

## Take it Easy
