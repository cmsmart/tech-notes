## Arrow fucntions



* We’ve lost function and {} because all of our callback functions are one liners.

* We’ve lost () around the argument list when there’s just one argument (rest arguments are an exception, eg (...args) => ...)

* We’ve lost the return keyword because when omitting {}, single line arrow functions perform an implicit return (these functions are often referred to as lambda functions in other languages). Implicit return only happens for single statement arrow functions. When arrow function is declared with {}, even if it’s a single statement, implicit return does not happen



There’s one caveat, however, with omitting {} from arrow functions – how do you return an empty object, eg {}?

```
    const emptyObject = () => {};
    emptyObject(); // ?
```
Unfortunately there’s no way to distinguish between empty block {} and an object {}. Because of that emptyObject() evaluates to undefined and {} interpreted as empty block. To return an empty object from fat arrow functions you have to surround it with brackets like so ({}):

```
    const emptyObject = () => ({});
    emptyObject(); // {}
```

---

### Lexical this

Each function in JavaScript defines its own this context, which is as easy to get around as it is annoying. The example below tries to display a clock that updates every second using jQuery:

```
    $('.current-time').each(function () {
    setInterval(function () {
        $(this).text(Date.now());
    }, 1000);
    });
```

When attempting to reference the DOM element this set by each in the setInterval callback, we unfortunately get a brand new this that belongs to the callback itself. A common way around this is to declare that or self variable:

```
    $('.current-time').each(function () {
    var self = this;

    setInterval(function () {
        $(self).text(Date.now());
    }, 1000);
    });
```

The fat arrow functions allow you to solve this problem because they don’t introduce their own this:

```
    $('.current-time').each(function () {
    setInterval(() => $(this).text(Date.now()), 1000);
    });
```

### Spread operator

Fat arrow functions don’t have their own this and arguments. Having said that, you can still get all arguments passed into the arrow functions using rest parameters (also known as spread operator):

```
    function log(msg) {
        const print = (...args) => console.log(args[0]);
        print(`LOG: ${msg}`);
    }   

    log('hello'); // LOG: hello
```


---

#### Examples of changes

```
    const square = function(a) {
        return a*a;
    }
``` 
ES6

```
    const square = (a) => {
            return a*a;
    }
```
or

```
    const square = a => a*a
```

---

```
    function getVerifiedToken(selector) {
    return getUsers(selector)
        .then(function (users) { return users[0]; })
        .then(verifyUser)
        .then(function (user, verifiedToken) { return verifiedToken; })
        .catch(function (err) { log(err.stack); });
    }
```

ES6 

```
    function getVerifiedToken(selector) {
    return getUsers(selector)
        .then(users => users[0])
        .then(verifyUser)
        .then((user, verifiedToken) => verifiedToken)
        .catch(err => log(err.stack));
    }
```


