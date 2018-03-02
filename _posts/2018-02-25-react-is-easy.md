---
layout: post
title:  "React is Easy, Game Development is Hard"
date:   2018-02-25 14:26:30 -0400
categories: blog
---

## Learning React? Make a game!

Are you currently using React in your projects? If not, stop here and go [check it out](https://reactjs.org/). It's an awesome Javascript library that is lightweight and allows for building up a component-based UI.

I have been poking around React documentation over the past few months and ,at first, I didn't enjoy it. My initial motivation for picking it up was a a work requirement. You can imagine that the initial tutorials I went through was a slog through new information and new ways to write old Javascript. Once I decided to ditch the "todo" tutorials and make a small game, the library's usefulness and versatility began to woo me.

After putting in some weekends developing a small roguelike dungeon crawler, I came to this conclusion: If you are working through the learning slog that comes with every new JS framework, making a game will help you through the most difficult parts and keep you engaged.

  The game logic required for even the simplest arcade entertainment will force you to dive deep into React’s anatomy; leaving you a foundational knowledge from which you can build larger web apps.

## The Challenge of Game Logic
Let’s quickly discuss game logic in order to better appreciate how it will influence our internalization of React later on. The most fundamental aspect of game architecture is the **game loop**.

> "The game loop is an important concept in any game, from the most low tech pong clong to a triple A graphics card melting FPS. An oversimplified version has three stages:

> 1. Take input from the player.

> 2. Change game state accordingly.

> 3. Display something to the player."

-- [James Nutt](https://jsrn.gitbooks.io/make-your-first-text-adventure-in-ruby/content/the_game_loop.html)

If you were to make a simple game right now, you would certainly build it in terms of these three steps. Let's examine the classic arcade game Galaga in these terms. In this game the player has three inputs, 'left', 'right', and 'shoot'. Step one of our game loop would listen for these inputs; say the player inputs 'left'. Step two of our game loop would change the space ship position variable accordingly. Step three of our game loop would actually draw the space ship to the screen in its new position. Games loops generally run at a rate of 60 frames per second, so the net visual effect to the screen would be a space ship quickly gliding to the left.

Now let's compare these steps of the generic game loop to the steps of a generic React component. The most common components will consist of three things: incoming data referred to as 'props' (or properties); a state which holds the current state of data passed in; and a render function that is responsible for using the data from state to display in terms of HTML.

Folks, that is the description of a proper game loop! After I realized how similar the component structure is to the game loop, learning React has been a blast because it allows me to practice new concepts in React expressed via simple web games.

## Forcing Your Focus

## Fundamentals as a Foundation

### Until Then

## Take it Easy
