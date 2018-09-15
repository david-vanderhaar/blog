---
layout: post
title:  "React is Easy, HOC's Are Hard"
date:   2018-09-15 14:26:30 -0400
categories: blog
---

*Although we are considering higher-order components in the context of ReactJS, the concept can be applied anywhere because it is based on a much broader functional programming technique called  [composition](https://hackernoon.com/functional-programming-paradigms-in-modern-javascript-function-composition-109670038859).*

## HOC's
A higher-order component is a **function** that **receives a component** and **returns a component**.

### Why
1. HOC's avoid code duplication
2. HOC's make components easy to read and easier to understand.
3. HOC's are reusable
4. HOC's can be combined

If even for only the reasons above, you should begin planning how you can use HOC's in your React flow.

Mehdi Mollaverdi gives [even more](http://rea.tech/reactjs-real-world-examples-of-higher-order-components/) specific reasons for implementing HOC's.


> 1. Do things before and/or after it calls that component
> 2. Avoid rendering the component if certain criteria is not met
> 3. Update the props passed to that component, or add new props
> 4. Transform the output of rendering a component (e.g. wrap with extra DOM elements, etc.)

His reasons will become more apparent with example so let's see how to structure our HOC.

### The Simple How
The simplest example of an HOC is one that does nothing! `Remember that HOC's aren't actually components`, they are functions that return components. Normally, we name these functions by stating what they add to the original component, preceded by 'with'. So our first HOC will be called `withNothing(originalComponent)`.

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

Next we write our simple HOC:

```
import React from 'react';

const withNothing = (originalComponent) => {
  class HOC extends React.Component {
    render() {
      return <originalComponent />;
    }
  }

  return HOC;
};
```

If we create a new component using our `<Hello />` component and `withNothing()`, it will simply return `<Hello />` as is. We can call it like so:
```
const resultingComponent = withNothing(<Hello />)
```

To kick it up a notch, let's create and HOC that add's a name div to `<Hello />`.

```
import React from 'react';

const withName = (originalComponent, namePassedIn) => {
  class HOC extends React.Component {
    constructor() {
      super();
      this.state = {
        name: namePassedIn,
      };
    }

    render() {
      return (
        <originalComponent />
        <div>{ this.state.name }</div>
      );
    }
  }

  return HOC;
};
```

If we create another new component using our `<Hello />` component and `withName()`, we can easily add a 'name' div to it and any other component that needed this information.

Calling like so:
```
const resultingComponent = withName(<Hello />, 'David')
```
eventually renders out to this:
```
<div>Hello</div>
<div>David</div>
```

### In Practice
I found a lot of examples of HOC's on the web. I'll summaraize some of them here and leave it for you to explore.

[**The React docs**](https://reactjs.org/docs/higher-order-components.html) describe a situation in which you have two components performing different API calls and rendering different outputs; yet  obtain and attach an change listener to the data identically.

[**Trey Huffine's article**](https://levelup.gitconnected.com/understanding-react-higher-order-components-by-example-95e8c47c8006) provides an awesome example of adding local storage functionality to several components. He creates an HOC that attaches `save()` `load()` and `remove()` methods to any component.

[Mehdi Mollaverdi's article](http://rea.tech/reactjs-real-world-examples-of-higher-order-components/) includes several examples. He makes interesting use of HOC's by wrapping each component in a `featureToggle()` HOC, which determines if that particular component should be rendered at all.

## Learn More About it
Here a few, great resources on the subject.

1. [React Documentation](https://reactjs.org/docs/higher-order-components.html)
2. [Understanding React Higher-Order-Components by Example](https://levelup.gitconnected.com/understanding-react-higher-order-components-by-example-95e8c47c8006)
3. [Real World Examples of Higher-Order Components](http://rea.tech/reactjs-real-world-examples-of-higher-order-components/)
4. [The original gist from Sebastian Markbåge](https://gist.github.com/sebmarkbage/ef0bf1f338a7182b6775)

### Until Next Time

## Take it Easy
