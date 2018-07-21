# The bindings

If you go to `EzInput/Data` you will see that there are a few Scriptable Objects there, you'll be modifying those (and creating more if needed) to fit your needs. The _Bindings_ file is where all your bindings will be stored. If you click on the _Bindings_ file and then "Add" in it's editor a new _binding_ will show up in the list. You can change the input type of the binding to be either a Button or an Axis. If you expand the binding you will be able to add _inputs_ to it by clicking the "Add" button. You can configure those inputs by expanding them.

!!! hint
    You can create a new bindings file through the Create menu.

!!! hint
    You can duplicate bindings by right-clicking them and clicking "Duplicate"

!!! note
    In the code we refer bindings as _binding groups_ and inputs as _bindings_. So a binding group has a name, a type and multiple bindings. We change the name in the UI to make it easier to understand.

### Button inputs

If you set the type of your binding to Button you can only add button inputs to your binding. By expanding an input you will be able to select a button. You can also have a key instead of a button, to do that check "Key as button" and select a key from the dropdown. You can also have an axis as a button by checking "Axis as button", selecting an axis from the dropdown and configuring a released/pressed zone. The button will be in the released state when the axis value is between 0 and the _released zone_ value. By checking "Invert?" the released zone becomes a _pressed zone_.

!!! note
    In case the selected axis for an axis as button has a negative value the value will be made positive. The value used when checking for the pressed/released zone is always positive. I.e. the value used is the absolute value from the axis.

### Axis bindings

If the binding type of your binding is set to Axis you can only have axis inputs. By expanding the inputs you can select an axis, add a deadzone to the axis and invert it. There is also the option to have a button or a key behave as an axis by checking either "Button as axis" or "Key as axis". Both behave the same way and have a pressed and released value.

!!! note
    The deadzone set in the input will be added to the deadzone set in the controller profile. Example: if the LeftStick_X axis has a 0.19 deadzone in the controller profile at use and your binding has a 0.1 deadzone then the actual deadzone of the LeftStick_X axis will be 0.29.

### The vale/state of a binding with multiple inputs

If you have a button binding with multiple inputs the binding state will be pressed if any of the input buttons are pressed. The axis bindings, on the other hand, add their input values together and clamp the value between -1 and 1. So if there's a binding with 3 inputs: two with a value of 1, and one with a value of 0 the binding value will be 1 (1 + 1 + 0 = 2, result value clamped between -1 and 1).