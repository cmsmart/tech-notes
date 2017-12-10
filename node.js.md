```yarn init```

will create a package.json file


add node montior tool

```yarn add nodemon --dev```

adds node_modules

---

run it 
```nodemon server.js ```

alternative  to actually find it
``` ./node_modules/.bin/nodemon ```

or add scripts to package json (node dev is naming convention server)

```
  "scripts": {
    "dev": "nodemon src/server.js"
  }
  ```

  and run it
  ``` yarn dev   ```


  ## This needs refinement

  ### Creating a new express project

* create a new folder
* ``` yarn init```  (create package.json)
* node files should have generally have files in a src file (like ruby apps)
* run ```yarn add express``` (creates node_modules and yarn.lock)
* create .gitignore and exclude node_modules (can also use gitignore extension in VSCode)
* add server.js with express set up
  in terminal run ```node src/server.js``` to start server
* Install nodemon (see above)


### mondodb

``` yarn add mongoose```

```sudo service mondod start```


  API

  yarn add body-parser
  see POST in .http