.. _ref_api_lua_modules:

``Creating Lua Modules``
========================

.. admonition:: TODO

    Finish examples and clear up the accompanying explanations.

The package library from the Lua 5.1 standard library provides an interface for
abstracting tables into neat APIs called modules [#]_. Lua's very own standard
library is implemented using modules. Modules can be used to create your own
APIs to use in your Lua devices.

In order for the Lua context to be able to find your modules, you must tell it
where to search for them. The package.path variable from the package module is a
specially formatted string of directory patterns that tells Lua where it should
search for a module.  You could set this in each file in which you use the
module, but it is much more convienent to create a Lua script and call
``dofile(...)``.

Example:
--------

config.lua
``````````

This script is located at the root of the plugin directory. You might also
consider placing it in a *Entry/* or *Scripts/* directory at the root of your
project.

::

  -- Here we set the package.path variable so the require() function can find
  -- our module. The package.path variable is string of directory patterns
  -- separated by semicolons. The pattern below searches in Cockpit/Scripts/
  -- a Cockpit/Scripts/SYSTEMS directory.
  if _G.package ~= nil and LockOn_Options ~= nil then
    _G.package.path = _G.package.path..';'..LockOn_Options.script_path.."/?.lua"
      ..';'..LockOn_Options.script_path.."SYSTEMS/?.lua"
  end

my_module.lua
`````````````

The script is located in the *Cockpit/Scripts/* directory.

::

  -- Edit the path below as necessary.
  dofile(LockOn_Options.script_path.."../../config.lua")

  -- The ellipsis captures the name of the script that defines the module
  -- (without the ".lua" extension"); in this case "my_module".
  local module_name = ...
  local module_table = { } -- Construct the module_table.

  -- Point the the global "my_module" to the module table.
  _G[module_name] = module_table

  -- Set "my_module" in the package.loaded table to reference our module table.
  -- This prevents us from needed to return our module table at the end of the
  -- script.
  package.loaded[module_name] = module_table

  -- The package excludes the global environment so any functions, tables, or
  -- variables you need must be "imported".
  local math = math
  local string = string
  local debug = debug
  local type = type
  local tostring = tostring

  -- The following line sets the environment to our module table, so we no
  -- longer have to prefix any functions, tables, or variables with the name of
  -- the table.
  setfenv(1, module_table)

  -- Example function(s) that will be exported with our module:
  function factorial(value)
    if value == 0 then return 1
    return value * factorial(value - 1)
  end

Using the Module in an avLuaDevice
``````````````````````````````````

The following is an example of using the module created above in an avLuaDevice
script.

::

  -- Edit the path below as necessary.
  dofile(LockOn_Options.script_path.."../../config.lua")

  local my_module = require('my_module')
  -- Code using the module...

.. [#] You can read more about modules in Chapter 15 of *Programming in Lua, 2nd
       Edition*.
