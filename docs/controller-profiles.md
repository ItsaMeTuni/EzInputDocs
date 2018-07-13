# Controller Profiles

If you go to `EzInput/Data` you will see that there are a few controller profile Scriptable Objects. Each of those files stores the button IDs for every button and axis of the controller. Since EzInput is based on Unity's native Input system EzInput needs this to get the correct button from the controller.  
If you open Edit->Project Settings->Input in the Editor and open a binding there you can see that there is an "Axis" dropdown with X, Y, 3rd Axis, 4th Axis, 5th Axis and so on. This is the ID of the axis (X is 1 and Y is 2). How about buttons? To get a joystick button in Unity's Input Manager you have to set "Positive button" to "joystick button 0" (where 0 is the ID of the button).  
So, basically, `ControllerProfile` files map those IDs to easily readable names (instead of configuring a binding to button 1 you configure it to Cross_A). Another positive side of this "mapping" is that you are able to set up many controllers in many platforms easily and separate the bindings themselves from the button and axis IDs.

!!! note
    The "Name" field is used by EzInput to find the correct `InputConfigs` file for the connected controller so that name has to be **exactly** the same as the controller name (you can find the controller name using `Input.GetControllerNames()`).

As you can see, configuring buttons are no mystery but configuring the axes and the D-Pad can get a bit complicated.

#### The D-Pad

D-Pads can be treated in two ways depending on the controller and the platform: they can be buttons (each DPad button has a button ID) or axes (one horizontal axis and one vertical axis). On Windows the XBox360 controller D-Pad is treated as a pair of axes (the horizontal and the vertical), so because of that we need to check "DPad is axis" and edit DPad horizontal and DPad vertical accordingly. If, for instance, your controller treats the D-Pad as buttons, uncheck "DPad is axis" and configure the button IDs in the Buttons section.

#### The Axes

Each axis has an ID, an input range, an output range and can be inverted. The ID and inversion of the value is pretty straight forward, but what are these input and output ranges? The input range is the value EzInput will receive from the controller and the output range is what you will get when you call `GetAxis()`. For example: in the PS4 controller on PC trigger values range from -1 to 1 (-1 being fully released and 1 being fully pressed) but it seems more logical to have it ranging between 0 and 1, don't you think? So we have to set "Min input range" to -1, "Max input range" to 1, "Min output range" to 0 and "Max output range" to 1.

## Creating a controller profile

To create a new controller profile file go to the Project tab in the Editor, right click, Create->EzInput->Controller Profile. 

## Setting the name of the controller
The profile stores the name of the controller it is for in the "Name" field (it's the first field in the controller profile editor, you'll find it). Be careful when setting the controller name because it has to match exactly the name of the controller. You can find the name of your controller in the [test scene](test-scene.md) or you can use `Input.GetJoystickNames()` and look into the string array it returns.

## Setting the platform of the profile
You can restrict a controller profile to a specific platform by selecting it in the "Target platform" field (you can also select multiple target platforms). Now, you'd probably be asking yourself why do this? The reason behind that is simple. Let's take the XBox 360 controller, in Windows the D-pad works as a pair of axes but in OSX the D-pad is treated as group of buttons. So if you had the same profile for Windows and OSX you'd get incorrect input from the same controller.

!!! note
    If the platform you're selecting is WindowsPlayer, OSXPlayer or LinuxPlayer dont forget to check their editor versions (WindowsEditor, OSXEditor, LinuxEditor). If you dont do this your controller profile won't work in the editor (but it will work on a build).

You'll also need to add it to the list in the EzInput prefab located at `EzInput/Resources`, if you don't EzInput won't even know it exists.

!!! warning
    Don't forget to add your new Controller Config file to the list in the EzInput prefab in `EzInput/Resources`. I know it's written on the line above but you might have skipped that part so here's a big orange warning to catch your attention and save you a headache. You're welcome :)

## Default Controller Profile

When you connect a controller EzInput tries to find a ControllerProfile that matches your controller and platform. If it can't find one it uses the default controller profile. The default controller profile is located at the EzInput prefab in `EzInput/Resources`.