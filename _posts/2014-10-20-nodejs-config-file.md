---
title: "Node.js Alternate Config File" 
excerpt: "An alternate config file in node for setting variables based on current env without the overhead of another library with more flexibility than a .json file."
categories:
  - JS
tags:
  - Reference
  - Node.js
toc: true
toc_sticky: true
---
Let me answer some questions to start with.

> Why not just use a config.json file and then require that?

1. You can't reference your NODE_ENV variable.
2. You can't require any additional files. What if you want to use reuse a field in an existing library's config file or from your package.json!?
3. You can't have ANY logic in a .json file.

> Why not just use another library?

1. You have a potentially unnecessary dependency.
2. You have less control.

Ok, so let's jump into an example. In the following example I have different values based on what the NODE_ENV variable is set to (or not set to). I also use the name in my package.json to decide what my database name will be set to on my local machine. I also have flexibility to not care whether you call an env prod or production. I also know exactly what is going on in this file and have no dependencies that I have to learn about.

```javascript
var npmInfo = require('./package.json');

module.exports = function(){
  console.log("Node Env Variable: " + process.env.NODE_ENV);

  // istanbul ignore next: don't look at the env variables
  switch(process.env.NODE_ENV){
    case null:
    case undefined:
    case "local":
      return {
        env: 'local', //should be env/prod
        dbURI : "mongodb://localhost/" + npmInfo.name,
        expressPort: 3000,
        loggerLevel: 'info'
      };
    case "dev":
    case "development":
      return {
        env: 'dev', //should be env/prod
        dbURI : process.env.MONGODB_URI,
        expressPort: process.env.PORT,
        loggerLevel: 'info'
      };
    case "test":
    case "testing":
      return {
        env: 'test', //should be env/prod, can be changed to prod when we are comfy with prod environ
        dbURI : process.env.MONGODB_URI,
        expressPort: process.env.PORT,
        loggerLevel: 'debug'

      };
    case "prod":
    case "production":
      return {
        env: 'prod', //should be env/prod, can be changed to prod when we are comfy with prod environ
        dbURI : process.env.MONGODB_URI,
        expressPort: process.env.PORT,
        loggerLevel: 'debug'

      };
    default:
      throw new Error("Environment Not Recognized");

  }
}();

```

In my app.js file I use this as such

```javascript
var config = require('./config.js');
config.expressPort; //this will be equal to 3000 for local env
```