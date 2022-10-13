.. _ref_api_show_param_handles_list:

``show_param_handles_list``
====================================

This function toggles an ImGui widget window that contains a list of parameter
handles and an interactive graph that displays their values.

.. admonition:: todo

    Insert an image of the ImGui widget in-game.

.. function:: show_param_handles_list(value)

   :param value: Optional boolean value to enable or disable the widget.
   :returns: Placeholder text.

Example:
--------
::

  -- In the context of an avLuaDevice:
  function post_initialize()
    --
    show_param_handles_list()
    --
    show_param_handles_list(false)
  end
