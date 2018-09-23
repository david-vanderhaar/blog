---
layout: post
title:  "React is Easy, Render Props Are Hard"
date:   2018-09-23 01:26:30 -0400
categories: blog
---

## Render Props in React
Using render props in your React app is a great way to reuse code and share functionality between components.

A render prop is a **function** that is passed to a component as a prop and **returns a render method**.

### Why
1. Render props avoid code duplication
2. Render props are reusable
3. Render props offer an alternative to using higher-order components

### The Simple How
Let's look at a simple example. Keep in mind that render props are just normal props. Instead of being a prop that holds data it is a function that returns data. The render prop is commonly named `render` but it can be named anything.

Let's say our original component is simply a div that says 'Hello'.
```
class Hello extends React.Component {
  render() {
    return (
      <div>Hello</div>
    );
  }
}
```

Our goal will be to dynamically add a `<Name />` component that displays our name based on some variable we pass in.

Next we write our simple Name component:
```
class Name extends React.Component {
  render() {
    const name = this.props.name;
    return (
      <div>{ name }</div>
    );
  }
}
```

Now let's update our `<Hello />` to incorporate a render prop:
```
class Hello extends React.Component {
  render() {
    return (
      <div>Hello</div>
      {this.props.render(this.state)}
    );
  }
}
```

Finally combining `<Hello />` and `<Name />`, we can create a new component like so:
```
class HelloWithName extends React.Component {
  render() {
    return (
      <div>
        <Hello render={name => (
          <Name name={name} />
        )}/>
      </div>
    );
  }
}
```
And eventually renders out to this:
```
<div>Hello</div>
<div>David</div>
```

This is example is not meant to be realistic, rather is is attempting to communicate the pattern of using render props. You can see that using a components prop as a function rather than a simple variable we can actually execute commonly used code within the render methods of multiple components.

Consider a situation in which you have multiple components calling to an API in the same way and handling the data identically. Perhaps you need to access local storage from multiple parts of your app.

Find the application that works best for you.

## Learn More About it
 For further exploration of this common pattern

1. [React Documentation](https://reactjs.org/docs/render-props.html)
2. [Understanding React Render Props by Example](https://levelup.gitconnected.com/understanding-react-render-props-by-example-71f2162fd0f2)

### Until Next Time

## Take it Easy
