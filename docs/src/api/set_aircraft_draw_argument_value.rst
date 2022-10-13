.. _ref_api_set_aircraft_draw_argument_value:

``set_aircraft_draw_argument_value``
====================================

This function can be used to set the value of external animations called
“arguments”.

.. function:: set_aircraft_draw_argument_value(argument, value)

   :param argument: The argument number (integer value).
   :param value: The value to apply to the argument number.
   :returns: No value.

Example:
--------
::

  -- In the context of an avLuaDevice:
  function update()
    -- Set the value of argument 0 (typically represents the position of the
    -- main gear).
    set_aircraft_draw_argument_value(0, 1.0)
  end
