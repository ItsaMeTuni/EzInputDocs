# Help

Here you can find solutions to errors you might encounter.

## EzInput is not detecting my controller profile

Make sure you added the controller profile to the "controller profiles" list in EzInput's prefab. You can find the prefab at `EzInput/Resources`.

## How do I change the bindings, controller profiles or default controller profile at runtime?

Take a look at [this](code-reference/#changing-bindings-controller-profiles-or-default-controller-profile-at-runtime).

## How about mouse input

Since mouse input doesn't change based on platform just use `Input.GetAxis("Mouse X")`, `Input.GetAxis("Mouse X")`, `Input.GetMouseButton()`, `Input.GetMouseButtonDown()`, `Input.GetMouseButtonUp()` (all from Unity's native `Input` class).

Didn't find a solution for your error/problem? Contact me at _lucasba8@gmail.com_.