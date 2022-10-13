.. _ref_api_get_aircraft_draw_argument_value:

``get_aircraft_draw_argument_value``
====================================

This function can be used to retrieve the value of external animations called
“arguments”.

.. function:: get_aircraft_draw_argument_value(argument)

   :param argument: The argument number (integer value).
   :returns: The current numerical value of the specified external argument.

Example:
--------
::

  -- In the context of an avLuaDevice:
  function update()
    -- Retrieve the value of argument 0 (typically represents the position of
    -- the main gear).
    local value = get_aircraft_draw_argument_value(0)
    print_message_to_user("Value of argument 0: "..tostring(value))
  end
