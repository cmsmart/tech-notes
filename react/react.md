# React

Create new react app

```yarn create react-app appname```

Or to install yarn on existing react

``` yarn install ```

Start server

```yarn start``` 



## Definitions

### Immutable

An element describes what you want to see on the screen:

```const element = <h1>Hello, world</h1> ```

React elements are immutable. Once you create an element, you can’t change its children or attributes.

### ComponentDidupdate / ComponentDidMount/Unmount (lifecycle hooks)

### Object.assign

### Fragment

To use add to component

``` import React, { Fragment }  from 'react' ```

Represents a minimal document object that has no parent. Can be used instead of div. 

eg

```
    function MyProducts({
        products
    }) {
        return (
            <div>
                {
                    products.map((product) => (
                        <Fragment key={ product._id }>
                            <Product
                            {...product}
                            />
                        </Fragment>
                    ))
                }
            </div>
        )
    }

```