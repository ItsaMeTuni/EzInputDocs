# The bindings

If you go to `EzInput/Data` you will see that there are a few Scriptable Objects there, you'll be modifying those (and creating more if needed) to fit your needs. The _Bindings_ file is where all your bindings will be stored. If you click on the _Bindings_ file and then "Add" in it's editor a new binding will show up in the list. You can change the input type of the binding to be either a Button or an Axis and configure it to your needs.

!!! note
    You can create a new bindings file through the Create menu.

### Button bindings

If you set the binding type to button you just need to select a button from the dropdown for your binding. The buttons available in the dropdown have names for the same positions in a PS4 controller or an XBox controller (Cross in a PS4 controller is equivalent to A in an XBox controller). You can also have use a keyboard ke, just check "Key as button" and then you will be able to select a key from the dropdown.  
There's also another possibility: turning an axis to a button. To do that check "Axis as button", select the axis you want in the dropdown and configure the "Released zone". The released zone determines when the button is at the released state, so if the modulus of the axis value (the square root of the axis value², making negative values positive) is smaller than the released zone the button will be in the released state, if greater then the button will be in the pressed state. If you want the "Released zone" to turn into a "Pressed zone" check "Invert?", it will work in "reverse" so when the modulus of the axis value is smaller than the "pressed zone" the button will be in the pressed state.

### Axis bindings

If the binding type of your binding is set to Axis there are a few options you can change. First, you can select an axis for your binding from the dropdown, then you can set a deadzone to it and invert it if you'd like.

!!! note
    The deadzone set in the bindings will be added to the deadzone set in the InputConfigs. Example: if the LeftStick_X axis has a 0.19 deadzone in the InputConfigs and your binding has a 0.1 deadzone then the actual deadzone of the LeftStick_X axis will be 0.29.

You can also make a button behave as an axis (i.e. when the button is pressed the axis binding value will be 1 and when the button is released the binding value will be 0). To do that just check "Button as axis", select a button and set the pressed and released values. If you want to make a key behave as an axis just check "Key as axis".

### Multiple bindings with the same name

If you want two buttons to do the same thing in your game you can have multiple bindings with the same name. When you call `GetButton("Jump", InputType.Hold)` true will be returned if any of the button bindings is pressed. The same can be done with `GetAxis`, but then the values of the axes will be added together and then the result value will be clamped between -1 and 1.
