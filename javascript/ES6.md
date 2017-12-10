
## ES6 / ECMA

## Variables

const variable = variables that shouldn't be reassigned

let variable = variables in block scoping

---


### Arrow functions and 'this' scope

* can help with the scope of this (ie don't require declaing this wthin the ForEach loop or .bind)

```
    var person = {
        first: "Doug",
        actions: ['bike', 'hike', 'ski', 'surf'],
        printActions() {
            this.actions.forEach(action => {
                var str = this.first + " likes to " + action;
                console.log(str);
            });
        }
    };
    person.printActions();
```

---

To read values from X and assign them to variables with the same name

e.g.

```const square = X.square```

can use destructured syntax

```const {square } = X ```
```const { PI, sum, square } = X ```

---



### Spread operator

* can turn elements of array into arguments of a function call

e.g. spread operator in animals array displays the full cats and dogs array

```
    var cats = ["Tabby", "Siamese", "Persian"];
    var dogs = ["Golden Retriever", "Pug", "Schnauzer"];

    var animals = ["Whale", "Giraffe", ...cats, "Snake", ...dogs, "Coyote"];

```

---


### Map

* Use something other than a string as a key e.g. a function, array, or number can be a key
* utilize key value pairs that are always the same values
* Need to iterate in order

---

### Template string

```console.log("Hello " + firstName)```

can be

```console.log(`Hello ${ firstName }`)```


// Basic literal string creation
``` `In JavaScript '\n' is a line-feed.` ```

// Multiline strings
```
    `In JavaScript template strings can run
    over multiple lines, but double and single
    quoted strings cannot.`
```

// String interpolation
```
    var name = 'Bob', time = 'today';
    `Hello ${name}, how are you ${time}?`
```

---

### Default parameters

```
    function haveFun(activityName="hiking", time=3) {
        console.log(`Today I will go ${activityName} for ${time} hours.`)
    }

    haveFun("biking", 5);
```

---

### Object literal

A JavaScript object literal is a comma-separated list of name-value pairs wrapped in curly braces.

 You should not use an object literal at the beginning of a statement. This will lead to an error or not behave as you expect, because the { will be interpreted as the beginning of a block.

e.g.

```
    var cat = {
        meow(times) {
            console.log("meow".repeat(times));
        },
        purr(times) {
            console.log("purr".repeat(times));
        },
        snore(times) {
            console.log("ZZZ".repeat(times));
        }
    };

    cat.meow(3);
    cat.purr(4);
    cat.snore(5);
```
e.g.

The following is an example of an object literal. The first element of the car object defines a property, myCar, and assigns to it a new string, "Saturn"; the second element, the getCar property, is immediately assigned the result of invoking the function (carTypes("Honda")); the third element, the special property, uses an existing variable (sales).

```
    var sales = 'Toyota';

    function carTypes(name) {
    if (name === 'Honda') {
        return name;
    } else {
        return "Sorry, we don't sell " + name + ".";
    }
    }

    var car = { myCar: 'Saturn', getCar: carTypes('Honda'), special: sales };

    console.log(car.myCar);   // Saturn
    console.log(car.getCar);  // Honda
    console.log(car.special); // Toyota
```


e.g.

```
    const PI = 3.14159
    const sum = (a,b) => (a + b)
    const square = a => a*a

    const X = {
        PI: PI,
        sum: sum,
        square: square
    }

```
can omit the values when the property name and the values are the same

```
    const X = {
        PI,
        sum,
        square
    }
```

---

### Destructuring assignment 

e.g.
* wrap variable names in curly braces to access properties : ({destination, activity})
* grabbing vacation object and passing it into the function so it can parse it : (vacationMarketing(vacation))

```
    var vacation = {
        destination: "Chile",
        travelers: 2,
        activity: "skiing", 
        cost: 4000
    };

    function vacationMarketing({destination, activity}) {
        return `Come to ${destination} and do some ${activity}`
    }

    console.log(vacationMarketing(vacation));
```

---

### Generators

Generators are a new type of function that allow us to pause functions in the middle of execution, to be resumed later. 

---

### Symbols

Symbols are often used as unique identifiers because they won't conflict with object keys that are strings. Symbols also help us to create customized iteration behavior

---

### Iterators


The iterable protocol which allows JavaScript objects to define or customize their own iteration behavior and the iterator protocol, a standard way to produce a sequence of values from a collection. 

An object is an iterator when it understands how to access each item in a collection. It also keeps track of where it is currently positioned in the collection. 

``` 
    var title = 'ES6';
    console.log(typeof title[Symbol.iterator]);
``` 

Symbol.iterator is a method that returns the default iterator for an object or a factory of iterators. So the type of title symbol iterator is going to be different. It's going to be a function. 



