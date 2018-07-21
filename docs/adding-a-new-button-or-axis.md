# Adding a new button or axis

If, for some reason, you need more buttons for your bindings you can go into `Scripts/DataTypes.cs` and add elements to the `ButtonCode` and `AxisCode` enums. Then you can go into your controller profiles and set the button and axis IDs there (EzInput will detect if you added buttons or axes to those enums). Then to use them in your bindings you just have to select them from the drop down when creating a binding.

!!! warning
    **DO NOT** remove any items from the enums that originally came with the package. Also, Be careful when _removing_ elements from the enums since EzInput can't know _which_ element you removed the IDs in the controller profiles might be shifted.

!!! warning
    After you added or removed an element from the enums open all controller profiles at least once so they can update themselves and prevent errors.

!!! warning
    When removing elements from the enums you might receive runtime errors if there is a binding that was using any of the elements.