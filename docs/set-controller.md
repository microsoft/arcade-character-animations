# set controller

Sets the controller that controls this sprite. When enabled, the directional buttons of the controller will set the facing direction of the sprite instead of the velocity and position changes.

```sig
characterAnimations.setController(
    sprites.create(img`.`, SpriteKind.Player),
    false
)
```

## Parameters

* **sprite**: the sprite to set the controller state for
* **enabled**: a boolean indicating if this sprite is controlled by buttons
* **controller**: an optional parameter that sets which player is controlling the sprite

```package
arcade-character-animations=github:microsoft/arcade-character-animations
```