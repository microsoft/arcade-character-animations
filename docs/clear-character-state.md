# clear character state

Clears the current state of a [sprite](/types/sprite).
If the state has been manually set, clearing the state will cause automatic state updates to start again.
This will also reset whatever direction the sprite is currently facing.

## Parameters

* **sprite**: a [sprite](/types/sprite) to clear the state of

## Example #example

In this example, press A to "lock" the character into the "MovingDown" state.
Press B to clear that state and automatically update the state again.

```blocks
controller.B.onEvent(ControllerButtonEvent.Pressed, function () {
    character.clearCharacterState(thePlayer)
    thePlayer.say("")
})
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    character.setCharacterState(thePlayer, character.rule(Predicate.MovingDown))
    thePlayer.say("LOCKED")
})
let thePlayer: Sprite = null
scene.setBackgroundColor(11)
thePlayer = sprites.create(img`
    . . . . . f f 4 4 f f . . . . .
    . . . . f 5 4 5 5 4 5 f . . . .
    . . . f e 4 5 5 5 5 4 e f . . .
    . . f b 3 e 4 4 4 4 e 3 b f . .
    . . f 3 3 3 3 3 3 3 3 3 3 f . .
    . f 3 3 e b 3 e e 3 b e 3 3 f .
    . f 3 3 f f e e e e f f 3 3 f .
    . f b b f b f e e f b f b b f .
    . f b b e 1 f 4 4 f 1 e b b f .
    f f b b f 4 4 4 4 4 4 f b b f f
    f b b f f f e e e e f f f b b f
    . f e e f b d d d d b f e e f .
    . . e 4 c d d d d d d c 4 e . .
    . . e f b d b d b d b b f e . .
    . . . f f 1 d 1 d 1 d f f . . .
    . . . . . f f b b f f . . . . .
    `, SpriteKind.Player)
character.loopFrames(
thePlayer,
[img`
    . . . . . f f 4 4 f f . . . . .
    . . . . f 5 4 5 5 4 5 f . . . .
    . . . f e 4 5 5 5 5 4 e f . . .
    . . f b 3 e 4 4 4 4 e 3 b f . .
    . . f 3 3 3 3 3 3 3 3 3 3 f . .
    . f 3 3 e b 3 e e 3 b e 3 3 f .
    . f 3 3 f f e e e e f f 3 3 f .
    . f b b f b f e e f b f b b f .
    . f b b e 1 f 4 4 f 1 e b b f .
    f f b b f 4 4 4 4 4 4 f b b f f
    f b b f f f e e e e f f f b b f
    . f e e f b d d d d b f e e f .
    . . e 4 c d d d d d d c 4 e . .
    . . e f b d b d b d b b f e . .
    . . . f f 1 d 1 d 1 d f f . . .
    . . . . . f f b b f f . . . . .
    `,img`
    . . . . . . . f f . . . . . . .
    . . . . . f f 4 4 f f . . . . .
    . . . . f 5 4 5 5 4 5 f . . . .
    . . . f e 4 5 5 5 5 4 e f . . .
    . . f b 3 e 4 4 4 4 e 3 b f . .
    . f e 3 3 3 3 3 3 3 3 3 3 e f .
    . f 3 3 e b 3 e e 3 b e 3 3 f .
    . f b 3 f f e e e e f f 3 b f .
    f f b b f b f e e f b f b b f f
    f b b b e 1 f 4 4 f 1 e b b b f
    . f b b e e 4 4 4 4 4 f b b f .
    . . f 4 4 4 e d d d b f e f . .
    . . f e 4 4 e d d d d c 4 e . .
    . . . f e e d d b d b b f e . .
    . . . f f 1 d 1 d 1 1 f f . . .
    . . . . . f f f b b f . . . . .
    `,img`
    . . . . . f f 4 4 f f . . . . .
    . . . . f 5 4 5 5 4 5 f . . . .
    . . . f e 4 5 5 5 5 4 e f . . .
    . . f b 3 e 4 4 4 4 e 3 b f . .
    . . f 3 3 3 3 3 3 3 3 3 3 f . .
    . f 3 3 e b 3 e e 3 b e 3 3 f .
    . f 3 3 f f e e e e f f 3 3 f .
    . f b b f b f e e f b f b b f .
    . f b b e 1 f 4 4 f 1 e b b f .
    f f b b f 4 4 4 4 4 4 f b b f f
    f b b f f f e e e e f f f b b f
    . f e e f b d d d d b f e e f .
    . . e 4 c d d d d d d c 4 e . .
    . . e f b d b d b d b b f e . .
    . . . f f 1 d 1 d 1 d f f . . .
    . . . . . f f b b f f . . . . .
    `,img`
    . . . . . . . f f . . . . . . .
    . . . . . f f 4 4 f f . . . . .
    . . . . f 5 4 5 5 4 5 f . . . .
    . . . f e 4 5 5 5 5 4 e f . . .
    . . f b 3 e 4 4 4 4 e 3 b f . .
    . f e 3 3 3 3 3 3 3 3 3 3 e f .
    . f 3 3 e b 3 e e 3 b e 3 3 f .
    . f b 3 f f e e e e f f 3 b f .
    f f b b f b f e e f b f b b f f
    f b b b e 1 f 4 4 f 1 e b b b f
    . f b b f 4 4 4 4 4 e e b b f .
    . . f e f b d d d e 4 4 4 f . .
    . . e 4 c d d d d e 4 4 e f . .
    . . e f b b d b d d e e f . . .
    . . . f f 1 1 d 1 d 1 f f . . .
    . . . . . f b b f f f . . . . .
    `],
100,
character.rule(Predicate.MovingDown)
)
character.loopFrames(
thePlayer,
[img`
    . . . . . f f 4 4 f f . . . . .
    . . . . f 5 4 5 5 4 5 f . . . .
    . . . f e 3 3 3 3 3 3 e f . . .
    . . f b 3 3 3 3 3 3 3 3 b f . .
    . . f 3 3 3 3 3 3 3 3 3 3 f . .
    . f 3 3 3 3 3 3 3 3 3 3 3 3 f .
    . f b 3 3 3 3 3 3 3 3 3 3 b f .
    . f b b 3 3 3 3 3 3 3 3 b b f .
    . f b b b b b b b b b b b b f .
    f c b b b b b b b b b b b b c f
    f b b b b b b b b b b b b b b f
    . f c c b b b b b b b b c c f .
    . . e 4 c f f f f f f c 4 e . .
    . . e f b d b d b d b b f e . .
    . . . f f 1 d 1 d 1 d f f . . .
    . . . . . f f b b f f . . . . .
    `,img`
    . . . . . . . . . . . . . . . .
    . . . . . f f 4 4 f f . . . . .
    . . . . f 5 4 5 5 4 5 f . . . .
    . . . f e 3 3 3 3 3 3 e f . . .
    . . f b 3 3 3 3 3 3 3 3 b f . .
    . . f 3 3 3 3 3 3 3 3 3 3 f . .
    . f b 3 3 3 3 3 3 3 3 3 3 b f .
    . f b b 3 3 3 3 3 3 3 3 b b f .
    . f b b b b b b b b b b b b f .
    f c b b b b b b b b b b b b f .
    f b b b b b b b b b b b b c f .
    f f b b b b b b b b b b c f . .
    . f c c c f f f f f f f e c . .
    . . . f b b d b d d e 4 4 e . .
    . . . f f 1 1 d 1 d e e f . . .
    . . . . . f b b f f f . . . . .
    `,img`
    . . . . . f f 4 4 f f . . . . .
    . . . . f 5 4 5 5 4 5 f . . . .
    . . . f e 3 3 3 3 3 3 e f . . .
    . . f b 3 3 3 3 3 3 3 3 b f . .
    . . f 3 3 3 3 3 3 3 3 3 3 f . .
    . f 3 3 3 3 3 3 3 3 3 3 3 3 f .
    . f b 3 3 3 3 3 3 3 3 3 3 b f .
    . f b b 3 3 3 3 3 3 3 3 b b f .
    . f b b b b b b b b b b b b f .
    f c b b b b b b b b b b b b c f
    f b b b b b b b b b b b b b b f
    . f c c b b b b b b b b c c f .
    . . e 4 c f f f f f f c 4 e . .
    . . e f b d b d b d b b f e . .
    . . . f f 1 d 1 d 1 d f f . . .
    . . . . . f f b b f f . . . . .
    `,img`
    . . . . . . . . . . . . . . . .
    . . . . . f f 4 4 f f . . . . .
    . . . . f 5 4 5 5 4 5 f . . . .
    . . . f e 3 3 3 3 3 3 e f . . .
    . . f b 3 3 3 3 3 3 3 3 b f . .
    . . f 3 3 3 3 3 3 3 3 3 3 f . .
    . f b 3 3 3 3 3 3 3 3 3 3 b f .
    . f b b 3 3 3 3 3 3 3 3 b b f .
    . f b b b b b b b b b b b b f .
    . f b b b b b b b b b b b b c f
    . f c b b b b b b b b b b b b f
    . . f c b b b b b b b b b b f f
    . . c e f f f f f f f c c c f .
    . . e 4 4 e d d b d b b f . . .
    . . . f e e d 1 d 1 1 f f . . .
    . . . . . f f f b b f . . . . .
    `],
100,
character.rule(Predicate.MovingUp)
)
character.loopFrames(
thePlayer,
[img`
    . . . . . . f f f f 4 4 f . . .
    . . . . f f b f 5 4 5 5 4 f . .
    . . . f b 3 3 e 4 5 5 5 5 f . .
    . . f b 3 3 3 3 e 4 4 4 e f . .
    . . f 3 3 3 3 3 3 3 3 3 3 f . .
    . . f 3 3 3 3 e b 3 e e 3 3 f .
    . . f 3 3 3 3 f f e e e 3 3 f .
    . . f b b b b f b f e e e 3 f .
    . . f b b b b e 1 f 4 4 e f . .
    . f f b b b b f 4 4 4 4 f . . .
    . f b b b b f f f e e e f . . .
    . . f b b f 4 4 e d d d f . . .
    . . . f f e 4 4 e d d d f . . .
    . . . . f b e e b d b d b f . .
    . . . . f f d 1 d 1 d 1 f f . .
    . . . . . . f f b b f f . . . .
    `,img`
    . . . . . . . . . . . . . . . .
    . . . . . . f f f f 4 4 f . . .
    . . . . f f b f 5 4 5 5 4 f . .
    . . . f b 3 3 e 4 5 5 5 5 f . .
    . . f b 3 3 3 3 e 4 4 4 e f . .
    . . f 3 3 3 3 3 3 3 3 3 3 3 f .
    . . f 3 3 3 3 e b 3 e e 3 3 f .
    . . f 3 3 3 3 f f e e e 3 3 f .
    . f f b b b b f b f e e e f . .
    . f b b b b b e 1 f 4 4 e . . .
    . f b b b b b f 4 4 4 4 f . . .
    . . f b b b 4 4 e d d d f . . .
    . . . f f f 4 4 e d d d f . . .
    . . . f b b e e b b d d d f . .
    . . . . f b d d 1 d 1 d b f . .
    . . . . . f f f b b f f f . . .
    `],
100,
character.rule(Predicate.MovingRight)
)
character.loopFrames(
thePlayer,
[img`
    . . . f 4 4 f f f f . . . . . .
    . . f 4 5 5 4 5 f b f f . . . .
    . . f 5 5 5 5 4 e 3 3 b f . . .
    . . f e 4 4 4 e 3 3 3 3 b f . .
    . . f 3 3 3 3 3 3 3 3 3 3 f . .
    . f 3 3 e e 3 b e 3 3 3 3 f . .
    . f 3 3 e e e f f 3 3 3 3 f . .
    . f 3 e e e f b f b b b b f . .
    . . f e 4 4 f 1 e b b b b f . .
    . . . f 4 4 4 4 f b b b b f f .
    . . . f e e e f f f b b b b f .
    . . . f d d d e 4 4 f b b f . .
    . . . f d d d e 4 4 e f f . . .
    . . f b d b d b e e b f . . . .
    . . f f 1 d 1 d 1 d f f . . . .
    . . . . f f b b f f . . . . . .
    `,img`
    . . . . . . . . . . . . . . . .
    . . . f 4 4 f f f f . . . . . .
    . . f 4 5 5 4 5 f b f f . . . .
    . . f 5 5 5 5 4 e 3 3 b f . . .
    . . f e 4 4 4 e 3 3 3 3 b f . .
    . f 3 3 3 3 3 3 3 3 3 3 3 f . .
    . f 3 3 e e 3 b e 3 3 3 3 f . .
    . f 3 3 e e e f f 3 3 3 3 f . .
    . . f e e e f b f b b b b f f .
    . . . e 4 4 f 1 e b b b b b f .
    . . . f 4 4 4 4 f b b b b b f .
    . . . f d d d e 4 4 b b b f . .
    . . . f d d d e 4 4 f f f . . .
    . . f d d d b b e e b b f . . .
    . . f b d 1 d 1 d d b f . . . .
    . . . f f f b b f f f . . . . .
    `],
100,
character.rule(Predicate.MovingLeft)
)
controller.moveSprite(thePlayer)

```

```package
arcade-story=github:microsoft/arcade-character-animations
```