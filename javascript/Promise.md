
### Promises

A Promise is an object representing the eventual completion or failure of an asynchronous operation.

Essentially, a promise is a returned object to which you attach callbacks, instead of passing callbacks into a function

Promises are asynchronous. Anything that need to wait for promise to proceed, you put that in .then.

The then() method returns a Promise. It takes up to two arguments: callback functions for the success and failure cases of the Promise.

The Promise.all() method returns a single Promise that resolves when all of the promises in the iterable argument have resolved or when the iterable argument contains no promises. It rejects with the reason of the first promise that rejects.

#### Promises are chainable.

A common need is to execute two or more asynchronous operations back to back, where each subsequent operation starts when the previous operation succeeds, with the result from the previous step. We accomplish this by creating a promise chain.

The then function returns a new promise, different from the original.

### Example

#### Create a promise

```
    /* ES5 */
    var isMomHappy = false;

    // Promise
    var willIGetNewPhone = new Promise(
        function (resolve, reject) {
            if (isMomHappy) {
                var phone = {
                    brand: 'Samsung',
                    color: 'black'
                };
                resolve(phone); // fulfilled
            } else {
                var reason = new Error('mom is not happy');
                reject(reason); // reject
            }

        }
    );
```

#### Consume a promise

```
    /* ES5 */
    ...

    // call our promise
    var askMom = function () {
        willIGetNewPhone
            .then(function (fulfilled) {
                // yay, you got a new phone
                console.log(fulfilled);
            // output: { brand: 'Samsung', color: 'black' }
            })
            .catch(function (error) {
                // oops, mom don't buy it
                console.log(error.message);
            // output: 'mom is not happy'
            });
    };

    askMom();

```

#### Chain promises

##### Create a second promise

```
    // 2nd promise
    var showOff = function (phone) {
        var message = 'Hey friend, I have a new ' +
                    phone.color + ' ' + phone.brand + ' phone';

        return Promise.resolve(message);
    };
```

##### Chain it

```
    // call our promise
    var askMom = function () {
        willIGetNewPhone
        .then(showOff) // chain it here
        .then(function (fulfilled) {
                console.log(fulfilled);
            // output: 'Hey friend, I have a new black Samsung phone.'
            })
            .catch(function (error) {
                // oops, mom don't buy it
                console.log(error.message);
            // output: 'mom is not happy'
    });
};

```