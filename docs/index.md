# Getting started

If you'd like, there is a video here[INSERT LINK] covering everthing in this page.

## The input manager asset file

The first thing you want to do when you import EzInput to your project is substitute the `InputManager.asset` file in your project's `ProjectSettings` folder with the file in `InputManager.zip`, that came with the EzInput. The reason for this is that EzInput uses Unity's built-in input manager but there is no way of accessing specific axes of specific controllers manually by code so we need to create roughly 250 (yeah...) entries in the input manager to be able to read those values. If you didn't get it, nervermind, just do it 🙂.

!!! warning
    you might want to make a backup of your `InputManager.asset` since you might want that input configuration back in case you decide not to use EzInput (not that there is a reason for taking a stupid decision as that 😅).

## Setting up the bindings

If you go to `EzInput/Data` you'll see there are a few Scriptable Objects there, you'll be modifying those (and creating more if needed) to fit your needs. The _EzInputBindings_ file is where all your bindings will be stored. If you click on the _EzInputBindings_ file and then "Add" in it's editor a new binding will show up in the list. You can change the input type of the binding to be either a Button or an Axis and configure it to your needs. You can read an in-depth review on the Bindings file [here](The-bindings.md).

## Reading the values through code

The best way to explain how to read values is by using examples, so here they are:

```csharp
//This will return true when the user presses the Cross button on a PS4 controller or A button on an XBox controller in any of the connected controllers
EzInput.GetButton(ButtonCode.Cross_A, InputType.Press, EzInput.ALL);

//This will return true if the left d-pad button is pressed down on the third controller (controller IDs are zero-based)
EzInput.GetButton("Jump", InputType.Hold, 2);

//This will return true when the "Jump" button binding is released on all controllers. Controller ID default to EzInput.All
EzInput.GetButton("Jump", InputType.Release);

//This will return a float value for the axis binding "Horizontal Movement". Again, Controller ID defaults to EzInput.All
EzInput.GetAxis("Horizontal Movement");

//This will return a float value for the axis binding "Vertical Movement" on the second controller.
EzInput.GetAxis("Vertical Movement", 1);

//This will return a float value for the left stick X axis on all controllers.
EzInput.GetAxis(AxisCode.LeftStick_X, EzInput.ALL);
```

Here's a table explaining the `InputType` enum:

`InputType`          | Unity equivalent
:--------------------|:-------------
`InputType.Hold`     |`Input.GetButton()`
`InputType.Press`    |`Input.GetButtonDown()`
`InputType.Release`  |`Input.GetButtonUp()`

!!! note
    Regarding the controller ID parameter in `GetButton` and `GetAxis`:  
    1. It is relative to `Input.GetJoystickNames()`  
    2. It is an optional parameter and will default to `EzInput.ALL` (getting input from all controllers)  
    3. it is zero-based  

!!! note
    When reading the input from all controllers (using `EzInput.ALL`):  
    - In the case of a `GetButton()` call the value returned will be true if the button is pressed in any controller  
    - In the case of a `GetAxis()` call the value returned will be the sum of the value of the axis on all controllers clamped between -1 and 1. For example: if there are three controllers with the axis at -1 then -1 * 3 = -3, clamp that between -1 and 1, the value returned will be -1.
    