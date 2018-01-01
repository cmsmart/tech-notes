# Node and React basic setup notes

## Set up new folder

``` mkdir <projectanme> ```

### Set up sub-folders

``` mkdir <api> ``` (for node)

``` mkdir <reactname> ``` (for react)

### cd into api directory

``` yarn init ```

### add standard modules

* --dev adds to dev dependencies

```yarn add nodemon --dev```

``` yarn add express body-parser mongoose ```

* create server.js file in api root and add 

```
    const express = require('express')
    const bodyParser = require('body-parser')

    const server = express()

    // Middleware Plugins (dependent)
    server.use(bodyParser.json())

    // Routes
    server.use('/', [
        require('./routes/<rootname>')
    ])

    // Start the server and set port
    server.listen(7000, (error) => {
        if (error) {
            console.error('error strating', error)
        }
        else {
            console.log('Started at http://localhost:7000')
        }
    })
```

### Add script to dependencies

```
    "scripts": {
        "dev": "nodemon src/server.js",
        "seed": "node src/models/seeds.js",
        "drop": "node src/models/drop.js"
    }

  ```

  ### Add .gitignore

  And add defaults using vscode .gitgnore extension from command palette
  
  Initiate git repo with 
  
  ``` git init ```


### Make sure mondgodb is going 

 ```sudo service mongod start``


 ### Make src foler and add models and routes folders inside

 ### Make check file and add a.http file for requests

 ## Create init.js file in models folder

```
    const mongoose = require('mongoose')

    // Use the Promise functionality built into Node.js
    mongoose.Promise = global.Promise

    // Connect to our local database
    mongoose.connect(
    'mongodb://localhost/<filename>',
    { useMongoClient: true }
    )
    .then(() => {
        console.log('Successfully connected to database')
    })
    .catch((error) => {
        // If there was an error connecting to the database
        console.error('Error connecting to MongoDB database', error)
    })

    module.exports = mongoose
```