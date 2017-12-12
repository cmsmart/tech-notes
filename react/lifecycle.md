# React Component Lifecycle

React enables to create components by invoking the React.createClass() method which expects a render method and triggers a lifecycle that can be hooked into via a number of so called lifecycle methods.

---

## The Lifecycle

### Initialization

The first two methods being called are getDefaultProps and getInitialState. Both methods are only called once when initially rendering the component.

Another two methods that only get called when initializing a component are componentWillMount and componentDidMount.

### componentWillMount

is called before the render method is executed

### Render 

The render method returns the needed component markup, which can be a single child component or null or false (in case you don't want any rendering).

This is the part of the lifecycle where props and state values are interpreted to create the correct output. Neither props nor state should should be modified inside this function. This is important to remember, as by definition the render function has to be pure, meaning that the same result is returned every time the method is invoked.

### componentDidMount 

The DOM can be accessed in this method, enabling to define DOM manipulations or data fetching operations. Any DOM interactions should always happen in this phase not inside the render method.

---

## State Changes

State changes will trigger a number of methods to hook into.

### shouldComponentUpdate

shouldComponentUpdate is always called before the render method and enables to define if a re-rendering is needed or can be skipped. Obviously this method is never called on initial rendering. A boolean value must be returned.

### componentWillUpdate

componentWillUpdate gets called as soon as the the shouldComponentUpdate returned true. Any state changes via this.setState are not allowed as this method should be strictly used to prepare for an upcoming update not trigger an update itself.

### componentDidUpdate

componentDidUpdate is called after the render method. Similar to the componentDidMount, this method can be used to perform DOM operations after the data has been updated.

---

## Props changes

Any changes on the props object will also trigger the lifecycle and is almost identical to the state change with one additional method being called.

### componentWillReceiveProps 

componentWillReceiveProps is only called when the props have changed and when this is not an initial rendering. componentWillReceiveProps enables to update the state depending on the existing and upcoming props, without triggering another rendering. One interesting thing to remember here is that there is no equivalent method for the state as state changes should never trigger any props changes.

---

## Unmounting 

The only method we haven't touched yet is the componentWillUnmount which gets called before the component is removed from the DOM. This method can be beneficial when needing to perform clean up operations, f.e. removing any timers defined in componentDidMount.

---

## Resources
[Understanding the React Component Lifecycle](http://busypeoples.github.io/post/react-component-lifecycle/)
[React.Component](https://reactjs.org/docs/react-component.html)