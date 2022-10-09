.. _ref_quickstart:

Quickstart
==========

So, you've probably reached this page because you have one question:
how do I get custom systems code in my mod? Well, look no further! We'll
do our best to try and break this down into a step-by-step process for you
to follow that's guaranteed to work.

Setting up
----------

First, we need to set up our mod's architecture to support systems coding.
Your structure should be updated to include the following paths:

.. code-block:: bash

    src/
    |_ Aircraft/
       |_ Cockpit/Scripts/
       |  |_ Systems/
       |  |_ device_init.lua
       |  |_ devices.lua
       |  |_ ...
       |_ entry.lua

As you may have noticed, there are three ``.lua`` files in the structure shown
above. Let's break down what needs to change in each one.

``entry.lua``
*************

The ``entry.lua`` file is responsible for declaring your DCS mod as a plugin
that can be used in-game. In your file, there will be an export function named
``make_flyable()``. We'll need to update it to appear like this:

.. code-block:: lua

    local self_ID = "Your mod name"
    local systems_path = current_mod_path .. "/Cockpit/Scripts"
    
    --- Makes an aircraft of self_ID flyable in DCS with the following arguments:
    --[[
        systems_path -  a string containing a path from the root of the directory
                        to your systems code.
        nil          -  this denotes whether you have .DLL binaries or not.
                        nil is a null placeholder in Lua. Use a string to reference
                        the name of your .DLL binary if you're working with an EFM.
        "/comm.lua"  -  a string contaniing a path from the root of the directory
                        to your qualifiers of the mod's conditions to the DCS engine.
    ]]--
    make_flyable(self_ID, systems_path, nil, current_mod_path .. "/comm.lua")
    plugin_done()

``devices.lua``
***************

``devices.lua`` is where all of our Lua devices are initialised. DCS uses
metatables to store Lua devices alongside an incremental counter function:

.. code-block:: lua

    count = 0

    function counter()
        count = count + 1
        return count
    end

    devices = {
        BASIC_SYSTEM = counter()
    }

``device_init.lua``
*******************

Once you initialise your Lua device in the appropriate file, you can now
declare it as its own:

.. code-block:: lua

    dofile(LockOn_Options.script_path .. "/devices.lua")
    local local_path = LockOn_Options.script_path .. "/Systems/"

    creators = {
        devices.BASIC_SYSTEM = {
            "avLuaDevice",
            local_path .. "basic_system.lua"
        }
    }

Now we've established our basic Lua device as a creatable device in the
initialiser file.

Creating a Lua device
---------------------

For demonstration purposes of this guide, we will be creating a basic Lua
device with :ref:`ref_api_avLuaDevice`.

Because we've went ahead and made a new Lua device named ``BASIC_SYSTEM``,
let's create a new file under ``Cockpit/Scripts/Systems/`` called
``basic_system.lua``.

.. admonition:: todo

    Write a thorough example of what ``basic_system.lua`` should look like.