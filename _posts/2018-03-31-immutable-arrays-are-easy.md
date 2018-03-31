---
layout: post
title:  "Arrays Are Easy, Immutability Are Hard"
date:   2018-03-31 14:26:30 -0400
categories: blog
---

## Immutable Arrays

If you find yourself using tools like React, Redux, or Vue when building web apps, you may have run into the concept of immutable data. At its core, this is the art of keeping your application's data clean. In general, it is good practice to and efficient to observe immutable data patterns in any app you are working on.

In javascript, arrays are essential so how can we keep them clean as pass them to and fro inside of our apps? An easy way to keep up with this kind of grunt work is to make sure we always return a new array. For example:

Instead of
```javascript
  let array = [1, 2, 3, 4]
  array.push(5)
  // array => [1, 2, 3, 4, 5]
```

We could do this
```javascript
  let array = [1, 2, 3, 4]
  let new_array = array.concat().push(5)
  // array => [1, 2, 3, 4]
  // new_array => [1, 2, 3, 4, 5]
```

This works without mutations because the `Array.concat()` function always returns a new array whereas `Array.push()` simply changes an array.

Here is a list of most of the `Array` function that return new arrays. As you move forward in your array-juggling journey, you can use this as a reference. Refer to the [MDN docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) for more details.

**Functions that return new arrays**
- `Array.of()`
- `Array.concat()`
- `Array.map()`
- `Array.filter()`
- `Array.slice()`

Use them to your advantage!

### Until Next Time

## Take it Easy
