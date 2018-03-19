---
layout: post
title:  "Cloning is Easy, Clones Are Hard"
date:   2018-03-15 14:26:30 -0400
categories: blog
---

## How Are You Cloning JS Objects?

Since delving into React and Redux I have learned the hard way how important immutability of data is. It is the very heart of Redux as well it breathes new life into React. In your own implementations of immutability you have probably used `Object.assign()` to create clones of of the objects holding your application's data.

Let's say we have library app that needs to keep track of book availability. In our example below, we use `Object.assign` to return a new `state` object with an updated `status` property.

```javascript
  function changeAvailability(book_id, new_availability) {
    return Object.assign({}, getBook(book_id), {
      availability: new_availability
    })
  }
```

Using `Object.assign()` in this way is ok, but we will see that this syntax quite cumbersome when writing more complicated functions. This is where [object spread syntax](https://github.com/tc39/proposal-object-rest-spread) comes in handy. Using the spread (...) operator in our previous function let's us simplify things.

```javascript
  function changeAvailability(book_id, new_availability) {
    return {...getBook(book_id), availability: new_availability}
  }
```

Now, what was once three lines and somewhat difficult to read, becomes singular and clean. Using spread syntax we were able to get rid of the surrounding parenthesis, the declaration of a new object, and the internal curly braces needed to update our object's properties.

`Object.assign()` is a function that can be difficult to pick out when skimming over code. We can observe in our fist example how easy it would be to miss the fact that an object is being return at all, since the `Object` function come right after the `return` statement. Our final example will demonstrate how easily one can pick up on object cloning, even in the middle of a function that composes more complex objects. The spread operator is easy to pick out and we immediately infer it's meaning.

```javascript
  function addBooksToBag(book_bag, new_book_ids = []) {
    return {...book_bag,
      books: [...books.push(
        new_book_ids.map(id => {getBook(id)})
      )]
    )}
  }
```

### Until Next Time

## Take it Easy
