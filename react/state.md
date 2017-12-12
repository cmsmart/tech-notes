# State

## Do Not Modify State Directly

The only place where you can assign this.state is the constructor.

``` 
    // Wrong
    this.state.comment = 'Hello';
```

```
    // Correct
    this.setState({comment: 'Hello'});

```


## State Updates May Be Asynchronous

Because this.props and this.state may be updated asynchronously, you should not rely on their values for calculating the next state.

```
    // Wrong
    this.setState({
    counter: this.state.counter + this.props.increment,
    });
```

To fix it, use a second form of setState() that accepts a function rather than an object. That function will receive the previous state as the first argument, and the props at the time the update is applied as the second argument:

```
    // Correct
    this.setState((prevState, props) => ({
    counter: prevState.counter + props.increment
    }));

```

## State Updates are Merged
