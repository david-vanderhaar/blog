---
layout: post
title:  "Testing is Easy, Anatomy is Hard"
date:   2018-06-02 14:26:30 -0400
categories: blog
---

- what is Jest
- the anatomy of a basic test
- making the addition test better

## The Anatomy of Good Jest Test

**First, a Gut-Check On the Importance of Testing**  
This post exists, mainly as an argument to myself. It's main purpose is to convince and remind that testing, as a development skill, is a valuable thing. So here is reinforcement from a seasoned developer [responding to the question, "Why do we write tests?"](https://www.youtube.com/watch?v=L5W9wSNnNqE&t=2518s)

>Because we want our **code to work**  
>Because we want it to **keep working**  
>Because we want to **develop faster**  
>Because we want to develop **with more confidence**  
>Because we make mistakes  
-- Elliotte Rusty Harold

**What is Jest?**  
Let's take a look at testing our javascript with this fantastic tool. It's great for testing JS in any environment whether it's vanilla or within a framework like React. In fact, Jest come out of the box when using create-react-app or react-native. It's fast and interactive giving you instant code coverage reports and information on failed tests. [Check it out here.](https://facebook.github.io/jest/) For this post we'll get started with testing our javascript by learning the basic anatomy of a good test as well as some things to look out for when writing tests, generally. Though we'll be working with Jest much of the information below applies to any test tool and language you use.

**Basic Anatomy**  
Every test should have three parts, each part answering these questions:
1. What component/method/function am I testing?
2. What aspect of this method am I testing?
3. What output do I expect?  

Let's go ahead and look at a primary Jest example, testing an addition function. We'll avoid file setup and configuration by using Jest at [repl.it](https://repl.it/languages/jest).

Here is the function being tested:
```
function add(a, b) {
  return a + b;
}
```
And here is the test written for it:
```
const add = require('./add');

describe('add', () => {
  it('should add two numbers', () => {
    expect(add(1, 2)).toBe(3);
  });
});
```
Though it is not a perfect test, it does answer the most important questions.  
1. The `describe()` answers the **first** question by declaring that it's testing the `add` function.  
2. The `it()` answers the **second** question by declaring that it `should add two numbers`  
3. The `expect()` and `toBe()` answer the **third** question by declaring that the output of 1 + 2 should be 3.

**Advanced Anatomy**  
By learning a bit of advanced Jest anatomy we can drastically improve this test, even revealing bugs in the process. A poorly-kept secret of the **second** question every test should answer is that you can, and should, ask it more than once per test.

If we look at our test again we see it `describe()` the add function by declaring that `it()` should add two numbers. Is there anything else `it()` should do? Is there anything `it()` should *not* do? What if we were to `add(1, '2')` where `1` is an integer and `'2'` is a string? JavaScript would return this as a string of `'22'` which is most likely not intended for our `add()` function. So let's reveal this bug in our code by adding to our test!

Let's ask what it should *not* do:

```
const add = require('./add');

describe('add', () => {
  it('should add two numbers', () => {
    expect(add(1, 2)).toBe(3);
  });
  it('should not add strings', () => {
    expect(add(1, '2')).toBe(null);
  });
});
```

And if we run our test now we get a different, more helpful output:

```
FAIL  ./add-test.js
  add
    ✓ should add two numbers (4ms)
    ✕ should not add strings (7ms)

  ● add › should not add strings

    expect(received).toBe(expected) // Object.is equality

    Expected value to be:
      null
    Received:
      "12"

    Difference:

      Comparing two different types of values. Expected null but received string.

      5 |   });
      6 |   it('should not add strings', () => {
    > 7 |     expect(add(1, '2')).toBe(null);
      8 |   });
      9 | });

      at Object.it (add-test.js:7:25)

Test Suites: 1 failed, 1 total
Tests:       1 failed, 1 passed, 2 total
Snapshots:   0 total
Time:        1.299s
Ran all test suites.
exit status 1
```

To finish up, let's correct our  `add()` to avoid this bug in the future:
```
function add(a, b) {
  if (typeof a !== 'number' || typeof b !== 'number') {
    return null
  }
  return a + b;
}
```

And now our tests pass! Can you think of other questions `it()` should be asking?

Again, here is the anatomy of a basic test:
1. What component/method/function am I testing?
2. What aspect of this method am I testing?
3. What output do I expect?  

The more you ask the better you'll be.

>A wise man can learn more from a foolish question than a fool can learn from a wise answer. – Bruce Lee

## Learn More About it

1. [Jest](https://facebook.github.io/jest/en/)
2. [5 Questions Every Unit Test Must Answer](https://medium.com/javascript-scene/what-every-unit-test-needs-f6cd34d9836d)
3. [Elliotte's Talk on Effective Unit Testing](https://www.youtube.com/watch?v=L5W9wSNnNqE&t=2518s)


### Until Next Time

## Take it Easy
