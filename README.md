Bring
=====

A little [node water](https://github.com/aogriffiths/node-wtr) to bring your modules to life.

"Bring" is inspired in some ways by the Java Spring framework. It hels you build 
easily configurable node applications based on modules your bring to life and link 
together.

For example:

    var bring = require('bring-modules');
    bring.autoconfigure();

Your application is now running! 


The Config File
---------------

Written in JSON config files have the following format:

At the top level there are three sections.

    config = {
      "require" :   required-modules,      //required
      "construct" : constructors           //required
      "templates" : template-constructors, //optional
    }


Requiring modules

    required-modules = {
      "<module-name>": module-options,
      ...    
    }

    module-options = {
      "depends": ["<module-name>", ...],
      "real-name": "<module-real-name>"
    }

Effectively this is just a wrapper for the require('<module-name>') function. 
When modules are required they are stored for later use under thier module-name. 

If you need to require a module but give it a name of your own use module-name with the
real-name option, where module-name is the name you want to give it and real-name is the name
you would pass to the require() function.

The depends array is a list of module-names that should be loaded before this module. It is
unlikely to be needed.


  
<module>:
  0..1 dependancies (array)

dependancies:
  0..1 dependancyname (string)


Made up of as many module:config elements as you need, where module is the name of the node module
you require and config currently takes one option:
