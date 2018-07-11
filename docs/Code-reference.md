#Code reference

Here you can find a list of methods to get the input data you desire:

```c#
bool GetButton(ButtonCode _button, InputState _state, int _controller = ALL)
```

```c#
bool GetButton(string _binding, InputState _state, int _controller = ALL)
```

```c#
float GetAxis(AxisCode _axisCode, int _controller = ALL)
```

```c#
float GetAxis(string _binding, int _controller = ALL)
```

`_controller` is the index of the controller you want to get the value from. If you want to get the value from all controllers use `EzInput.ALL`.  

!!! note
    The `_controller` parameter is zero-based e.g. the ID of the third controller is 2).

`_binding` the name of the binding in the Bindings Scriptable Object you wish to get the value from.  
`_button` the button you want to get the value from.  
`_axis` the axis you want to get the value from.  

!!! note
    `GetAxis` will **always** return a value between -1 and 1. However, this doesn't mean that if the axis can output a negative value. Depending on your Controller Config and the axis you're read it will or won't be able to output negative values. E.g. if configured accordingly a trigger will output 0 when released and a 1 when pressed.

!!! note
    All these methods are static so you can call `EzInput.Getbutton`.

!!! warning
    Don't forget to declare that you're using the `EzInputManager` namespace at the top of your .cs file like `using EzInputManager`.