---
layout: post
title:  "Variables are Easy, Declaring Them is Hard"
date:   2018-06-30 14:26:30 -0400
categories: blog
---

## Var . Let . Const
Javascript gives us three distinct ways to declare a variable. Those are `var` `let` and `const`. It can be difficult to know why or when to use one over the other. In the following examples we will discover that these key words are differentiated by the **scope** in which the act and the the behavior in which they **assign value**.

### Let's Talk scope
When using `var` we create variable that is _global_. This means we will always have access to it within the function it was declared. Its scope is _function level_.

`let` and `const` on the other hand are _block level_ scoped. This means that once declared inside of any block of code they cannot be accessed outside of that block. In the following example we'll declare a `var`, `let`, and `const` variable inside of the same block of code;

```
for (let miles = 0; miles <= 5; miles++) {
  const runner = 'Dakari';
  var kilometers = miles * 1.6;
  console.log(runner); //=> 'Dakari'
  console.log(miles); //=> 5
  console.log(kilometers); //=> 8
}

console.log(runner); //=> Uncaught ReferenceError: i is not defined
console.log(miles); //=> Uncaught ReferenceError: i is not defined
console.log(kilometers); //=> 8 Still accessible!
```

Now let's move our `const` outside of the `for` block. With that we get almost the same results except `runner` can be accessed after our block of our code.

```
const runner = 'Dakari';

for (let miles = 0; miles <= 5; miles++) {
  var kilometers = miles * 1.6;
  console.log(runner); //=> 'Dakari'
  console.log(miles); //=> 5
  console.log(kilometers); //=> 8
}

console.log(runner); //=> 'Dakari'
console.log(miles); //=> Uncaught ReferenceError: i is not defined
console.log(kilometers); //=> 8 Still accessible!
```

### Let's Talk Assignment
The last difference we'll point out here is in how we assign values to variables when declaring them in there three different manners. In this case `const` stands alone. Once you define a variable using `const` it can no long be re-assigned.

Let's say we assign my opinion on a certain pizza topping to a `const` variable.

```
const opinion = 'pineapple on pizza is good';
```

Now whether or not you agree, my opinion can't be changed! Go ahead... try it.
```
const opinion = 'pineapple on pizza is good';

opinion = 'pineapple on pizza is disgusting'; //=> Uncaught SyntaxError: Identifier 'opinion' has already been declared
```

To finish off, here's an amazing graphic to summarize what we just learned.

![Image](https://pbs.twimg.com/media/CzLVVjtXAAERmbc.jpg)

>A wise man can learn more from a foolish question than a fool can learn from a wise answer. – Bruce Lee

## Learn More About it

1. [Progamming with Mosh - Let vs Var](https://www.youtube.com/watch?v=XgSjoHgy3Rk)

### Until Next Time

## Take it Easy
