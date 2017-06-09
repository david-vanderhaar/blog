---
layout: post
title:  "Arrays are Easy, Cont."
date:   2017-06-09 00:00:00 -0400
categories: blog
---
## Saving the Good Ones for Arrainy Day

Last week we peeked at the map() function used on javascript arrays. Let's take look what reduce() can do for us.

Our reduce() function, like map(), iterates over each element of an array. But unlike map(), which returns a new array out of the function passed through it, reduce() combines and returns a single value from the array it was called on. It does this by taking in the previous index and current index as it iterates.

A simple use of reduce would be to add an array of numbers together.

	var num = [1,2,3,4,5];

	var total = num.reduce(function(previous, current){
			console.log(previous + '+' + current);
			return previous + current;
		});

Under the hood of this code, reduce is starting at num[0], in this case there is no previous value, so previous == 0 :

	// Console logs will give us:
	
	0 + 1 //previous is now 1
	1 + 2 //previous is now 3
	3 + 3 //previous is now 6
	6 + 4 //previous is now 10
	10 + 5 //previous is now 15

The final return is 15. There are so many great applications of reduce(), Let's learn them together!

Here a few [practical examples](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce?v=control) from Mozilla

Remember to look into filter() as well!

### Until Next Time

### Take it Easy

