## Function declaration vs function expression

* Badly placed Function Declarations are misleading and there are few (if any) situations where you can’t use a Function Expression assigned to a variable instead.


### Function Declaration

A **Function Declaration** defines a named function variable without requiring variable assignment. Function Declarations occur as standalone constructs and cannot be nested within non-function blocks.

A function created with a function declaration is a Function object and has all the properties, methods and behavior of Function objects.

```
    function bar() {
        return 3;
    }
```
The function name is visible within it’s scope and the scope of it’s parent (which is good because otherwise it would be unreachable)

eg

```
    function bar() {
        return 3;
    }
    
    bar() //3
    bar   //function
```
---

### Function Expression

A **Function Expression** defines a function as a part of a larger expression syntax (typically a variable assignment ). Functions defined via Functions Expressions can be named or anonymous. Function Expressions must not start with “function”. The function name (if any) is not visible outside of it’s scope (contrast with Function Declarations).

The main difference between a function expression and a function statement is the function name, which can be omitted in function expressions to create anonymous functions. 

eg

```
    //anonymous function expression
    var a = function() {
        return 3;
    }
    
    //named function expression
    var a = function bar() {
        return 3;
    }
    
    //self invoking function expression
    (function sayHello() {
        alert("hello!");
    })();

```
---

### Hoisting


For functions, only the function declaration gets hoisted to the top and not the function expression.

Function declarations and function variables are always moved (‘hoisted’) to the top of their JavaScript scope by the JavaScript interpreter.

Function expressions in JavaScript are not hoisted, unlike function declarations. You can't use function expressions before you define them.


### Context

#### LexicalEnvironment, VariableEnvironment and ThisBinding