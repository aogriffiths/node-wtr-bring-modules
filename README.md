```
                                 .("""")                                      (j)
                               (_(_ __(_ )                                 (n o d e)
 _ _ _       _                   / / /                       (n)              (s)
 ))`)`) ___  )L __ __           / / /           n            \|/              \|/
((,(,' ((_( (( (('(|             n             \|/            |                |
```
Part of the [Node Water](https://github.com/aogriffiths/node-wtr) collection. 

* __bring-modules__ - Bring your node.js modules to life.
    * On [github.com](https://github.com/aogriffiths/node-wtr-bring-modules)
    * On [npmjs.org](https://npmjs.org/package/bring-modules)
        
So What Does it Do?!
--------------------

"Bring" follows an inversion of control pattern similar to Java Spring.
It helps you easily build applications from modules which you link together using 
configuration, not code.

At runtime Bring reads your configuration file(s) and instantiates the modules that are
specified. It sets options, calls functions on those modules and can pass refences 
between them or to your main application. Using bring you can have an application
bootstrapped, up and running almost entirely by configuration. This is great if you want to 
"mix" different varients of your application or run your application with different 
configurations in different environments.

For example:

````js
var bring = require('bring-modules');
bring.autoconfigure();
````

Your application is now running! 

Installation
------------

Official releases can be obtained from:
* __github.com__ - the [tags section](https://github.com/aogriffiths/node-wtr-bring-modules/tags) 
                   provides links to zip or tar.gz packages. 
* __npm__        - use `npm install bring-modules`

The lastest developed code may node have not have been released, but can always be found
from:
* __github.com__ - the [project homepage](https://github.com/aogriffiths/node-wtr-bring-modules)
                   provides links to all the source code, branches and issue tracking.

The Config File
---------------

Bring configuration is a JSON object in the following format.

### Top Level

At the top level there are three sections, require, construct and templates.

````js
config = {
  "require" :   required-modules,      //required. (see Requiring Modules)
  "construct" : constructors,          //required. (see Constucting Modules)
  "templates" : template-constructors  //optional. (see Templates)
}
````

### Requiring Modules

````js
required-modules = {
  "<module-name>": module-options,
  ...    
}

module-options = {
  "depends": ["<module-name>", ...],
  "real-name": "<module-real-name>"
}
````

Effectively this a wrapper for the `require()` function with a few extra options:

* __required-modules__ - Object. With 1..\* properties:

    * __\<module-name\>__ - Object. Modules are stored for later use to module-names need 
      to be unique. Unless real-name is also give, module-name is also the string passed to 
      require e.g. `require('<module-name>')`.

* __module-options__ - Object. With 2 properties:
    * __depends__ - Array. Lists the module-names that should be loaded before this module. 
    * __real-name__ - String. If you need to give a module your own name use this option. 
      Make module-name the name you want to use it and real-name is the name you would 
      normall pass to the `require()` function.

### Constucting Modules

````js
constructors = {
  "< >":  ,
  ...    
}
````
TODO

### Templates

````js
template-constructors = {
  "< >":  ,
  ...    
}
````

TODO