# lock facing direction

Locks the direction that the sprite is facing to the specified direction. While locked, the sprite will always be facing that direction regardless of movement or controller input.

```sig
characterAnimations.lockFacingDirection(
    sprites.create(img`.`, SpriteKind.Player),
    characterAnimations.FacingDirection.Up
)
```

## Parameters

* **sprite**: the sprite to lock the facing direction of
* **direction**: the direction to lock the sprite's facing state in

```package
arcade-character-animations=github:microsoft/arcade-character-animations
```