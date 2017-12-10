# Control flow and error handling

## Block statement

The most basic statement is a block statement that is used to group statements.

Block statements are commonly used with control flow statements (e.g. if, for, while).

The block is delimited by a pair of curly brackets:

```
    {
        statement_1;
        statement_2;
        statement_n;
    }
```
---

## Conditional statements

A conditional statement is a set of commands that executes if a specified condition is true. JavaScript supports two conditional statements: if...else and switch.

#### if...else
* Multiple statements need curly braces
e.g.

``` 
    if (condition) execute-this-when-true 
```
vs

```
    if (condition) {
        execute_this;
        execute_this;
    }
    else {
        do_this;
    }
```

If you need to use an assignment in a conditional expression, a common practice is to put additional parentheses around the assignment.

```
    if ((x = y)) {
    /* statements here */
    }
```

##### Falsy values

The following values evaluate to false (also known as Falsy values):

* false
* undefined
* null
* 0
* NaN
* the empty string ("")


#### Switch statement

* break statement after each case to execute if condition met
* default is optional

```
    switch (expression) 
    {
        case value-1: statement-to-execute; break
        case value-2: statement-to-execute; break
        default: statement 
    }
```

---

## Exception handling statements

You can throw exceptions using the throw statement and handle them using the try...catch statements.

#### throw statement

Use the throw statement to throw an exception. When you throw an exception, you specify the expression containing the value to be thrown.

#### try...catch statement

The try...catch statement marks a block of statements to try, and specifies one or more responses should an exception be thrown. If an exception is thrown, the try...catch statement catches it.

#### The finally block

The finally block contains statements to execute after the try and catch blocks execute but before the statements following the try...catch statement. The finally block executes whether or not an exception is thrown. If an exception is thrown, the statements in the finally block execute even if no catch block handles the exception.

---

## Promises (see Promise.md)

The Promise object represents the eventual completion (or failure) of an asynchronous operation, and its resulting value.

Promise objects allow you to control the flow of deferred and asynchronous operations.

``` new Promise( /* executor */ function(resolve, reject) { ... } ); ```

A Promise is in one of these states:

* pending: initial state, not fulfilled or rejected.
* fulfilled: successful operation
* rejected: failed operation.
* settled: the Promise is either fulfilled or rejected, but not pending.
