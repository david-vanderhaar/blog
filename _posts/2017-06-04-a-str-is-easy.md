---
layout: post
title:  "Arrays are Easy, Array Functions are Hard"
date:   2017-06-04 20:00:00 -0400
categories: blog
---
## Saving the Good Ones for Arrainy Day

Hi everbody! This week I'm going to highlight a few, handy array functions. Let's not mince words here, _arrays are life_. As developers, the more comfrotable we are with arrays, the happier we'll be. Better array handling will improve organization, readability, and speed. I have come to understand arrays as basically lists of numbers, strings, or other things. The analogy I use, in my head, involves cardboard boxes and moving trucks. Instead of ordering my computer to take one number and move it somewhere else, I can order my computer to take a whole box of numbers and move them all at once. The box can be as big as I like and that is convenient. But, as we all know, packing things into a box isn't nearly as difficult as sorting through it once it's been stored and forgotten. When we work with arrays, this is what we're doing. We pack numbers or words, or colors into a box, then we move the box, and then we open the box, and then we get lost in the box!

Fortunately javascript provides us with some helpful functions to do the sorting. Today I'll go over the map() function, but keep an eye out for reduce() and filter().

As a simple default, I handle arrays with for loops. They're easy to read and easy to write. Here's an example where I will asign a random number to each item in our array.

	var array = [0,0,0,0,0];

	for (var i = 0; i < array.length; i++) {
		array[i] = Math.floor(Math.random() * 11);   // returns a number between 0 and 10
	}	

Now, let's say this returns our array as:
	
	[2,5,8,1,9,];

Great, we have our array filled with five random numbers between 0 and 10. But what if we want to build on that? Let's say  we have a client demanding that we store the square root of each number in our array. Well, of course we could go for the _for_ loop again:

	for (var i = 0; i < array.length; i++) {
		array[i] = Math.sqrt(array[i]);
	}	

Well, thats cool. Just do a little copy/pasting and we're golden. But eventually you'll come to a point where your array is interacting with other data in such a way that it will be hard to keep track of its length and how its been affected by other methods you've created.

A simpler way to perform the same job uses the map() function:

	array.map(Math.sqrt);

Wow, map() just did exactly what we told it to and nothing else. It takes every element of our array and applies the function we pass into it. We can even pass in pur own methods. The beauty of map() is that it applies a function to every element of an array, and __only__ every element of an array. We can always be sure it will never try to apply something to an element that doesnt exist.

Here a few [practical examples](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map?v=control) from Mozilla

Remember to look into reduce() and filter() as well!

### Until Next Time

### Take it Easy