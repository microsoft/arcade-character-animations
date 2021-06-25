# loop character animation

Adds an animation to a [sprite](/types/sprite) that will loop whenever the given rule is true.
If there are multiple animations with rules that match a sprite's current state, the most specific rule will win.
If the given rule is invalid (e.g. "Moving and NotMoving") then the animation will be ignored.

If another animation is registered using run frames with a rule that also matches the given state,
the animation will start looping after the other animation has completed.

```sig
character.loopFrames(
sprites.create(img`
    .
    `,
    [img`
    .
    `],
    500,
character.rule(Predicate.NotMoving)
)
```

## Parameters

* **sprite**: a [sprite](/types/sprite) the sprite to loop the animation on
* **animation**: the animation to loop when the given rule becomes true
* **interval**: the number of milliseconds to spend on each frame of the animation before advancing to the next
* **rule**: a rule that controls when the animation will loop on the sprite

## Example #example

In this example, we create a simple walking animation for our character in all four directions.

```blocks
scene.setBackgroundColor(7)
let thePlayer = sprites.create(img`
    . . . . . . f f f f . . . . . .
    . . . . f f f 2 2 f f f . . . .
    . . . f f f 2 2 2 2 f f f . . .
    . . f f f e e e e e e f f f . .
    . . f f e 2 2 2 2 2 2 e e f . .
    . . f e 2 f f f f f f 2 e f . .
    . . f f f f e e e e f f f f . .
    . f f e f b f 4 4 f b f e f f .
    . f e e 4 1 f d d f 1 4 e e f .
    . . f e e d d d d d d e e f . .
    . . . f e e 4 4 4 4 e e f . . .
    . . e 4 f 2 2 2 2 2 2 f 4 e . .
    . . 4 d f 2 2 2 2 2 2 f d 4 . .
    . . 4 4 f 4 4 5 5 4 4 f 4 4 . .
    . . . . . f f f f f f . . . . .
    . . . . . f f . . f f . . . . .
    `, SpriteKind.Player)
character.loopFrames(
thePlayer,
[img`
    . . . . . . f f f f f f . . . .
    . . . . f f e e e e f 2 f . . .
    . . . f f e e e e f 2 2 2 f . .
    . . . f e e e f f e e e e f . .
    . . . f f f f e e 2 2 2 2 e f .
    . . . f e 2 2 2 f f f f e 2 f .
    . . f f f f f f f e e e f f f .
    . . f f e 4 4 e b f 4 4 e e f .
    . . f e e 4 d 4 1 f d d e f . .
    . . . f e e e 4 d d d d f . . .
    . . . . f f e e 4 4 4 e f . . .
    . . . . . 4 d d e 2 2 2 f . . .
    . . . . . e d d e 2 2 2 f . . .
    . . . . . f e e f 4 5 5 f . . .
    . . . . . . f f f f f f . . . .
    . . . . . . . f f f . . . . . .
    `,img`
    . . . . . . . . . . . . . . . .
    . . . . . . f f f f f f . . . .
    . . . . f f e e e e f 2 f . . .
    . . . f f e e e e f 2 2 2 f . .
    . . . f e e e f f e e e e f . .
    . . . f f f f e e 2 2 2 2 e f .
    . . . f e 2 2 2 f f f f e 2 f .
    . . f f f f f f f e e e f f f .
    . . f f e 4 4 e b f 4 4 e e f .
    . . f e e 4 d 4 1 f d d e f . .
    . . . f e e e e e d d d f . . .
    . . . . . f 4 d d e 4 e f . . .
    . . . . . f e d d e 2 2 f . . .
    . . . . f f f e e f 5 5 f f . .
    . . . . f f f f f f f f f f . .
    . . . . . f f . . . f f f . . .
    `,img`
    . . . . . . f f f f f f . . . .
    . . . . f f e e e e f 2 f . . .
    . . . f f e e e e f 2 2 2 f . .
    . . . f e e e f f e e e e f . .
    . . . f f f f e e 2 2 2 2 e f .
    . . . f e 2 2 2 f f f f e 2 f .
    . . f f f f f f f e e e f f f .
    . . f f e 4 4 e b f 4 4 e e f .
    . . f e e 4 d 4 1 f d d e f . .
    . . . f e e e 4 d d d d f . . .
    . . . . f f e e 4 4 4 e f . . .
    . . . . . 4 d d e 2 2 2 f . . .
    . . . . . e d d e 2 2 2 f . . .
    . . . . . f e e f 4 5 5 f . . .
    . . . . . . f f f f f f . . . .
    . . . . . . . f f f . . . . . .
    `,img`
    . . . . . . . . . . . . . . . .
    . . . . . . f f f f f f . . . .
    . . . . f f e e e e f 2 f . . .
    . . . f f e e e e f 2 2 2 f . .
    . . . f e e e f f e e e e f . .
    . . . f f f f e e 2 2 2 2 e f .
    . . . f e 2 2 2 f f f f e 2 f .
    . . f f f f f f f e e e f f f .
    . . f f e 4 4 e b f 4 4 e e f .
    . . f e e 4 d 4 1 f d d e f . .
    . . . f e e e 4 d d d d f . . .
    . . . . 4 d d e 4 4 4 e f . . .
    . . . . e d d e 2 2 2 2 f . . .
    . . . . f e e f 4 4 5 5 f f . .
    . . . . f f f f f f f f f f . .
    . . . . . f f . . . f f f . . .
    `],
200,
character.rule(Predicate.MovingRight)
)
character.loopFrames(
thePlayer,
[img`
    . . . . . . f f f f . . . . . .
    . . . . f f f 2 2 f f f . . . .
    . . . f f f 2 2 2 2 f f f . . .
    . . f f f e e e e e e f f f . .
    . . f f e 2 2 2 2 2 2 e e f . .
    . . f e 2 f f f f f f 2 e f . .
    . . f f f f e e e e f f f f . .
    . f f e f b f 4 4 f b f e f f .
    . f e e 4 1 f d d f 1 4 e e f .
    . . f e e d d d d d d e e f . .
    . . . f e e 4 4 4 4 e e f . . .
    . . e 4 f 2 2 2 2 2 2 f 4 e . .
    . . 4 d f 2 2 2 2 2 2 f d 4 . .
    . . 4 4 f 4 4 5 5 4 4 f 4 4 . .
    . . . . . f f f f f f . . . . .
    . . . . . f f . . f f . . . . .
    `,img`
    . . . . . . . . . . . . . . . .
    . . . . . . f f f f . . . . . .
    . . . . f f f 2 2 f f f . . . .
    . . . f f f 2 2 2 2 f f f . . .
    . . f f f e e e e e e f f f . .
    . . f f e 2 2 2 2 2 2 e e f . .
    . f f e 2 f f f f f f 2 e f f .
    . f f f f f e e e e f f f f f .
    . . f e f b f 4 4 f b f e f . .
    . . f e 4 1 f d d f 1 4 e f . .
    . . . f e 4 d d d d 4 e f e . .
    . . f e f 2 2 2 2 e d d 4 e . .
    . . e 4 f 2 2 2 2 e d d e . . .
    . . . . f 4 4 5 5 f e e . . . .
    . . . . f f f f f f f . . . . .
    . . . . f f f . . . . . . . . .
    `,img`
    . . . . . . f f f f . . . . . .
    . . . . f f f 2 2 f f f . . . .
    . . . f f f 2 2 2 2 f f f . . .
    . . f f f e e e e e e f f f . .
    . . f f e 2 2 2 2 2 2 e e f . .
    . . f e 2 f f f f f f 2 e f . .
    . . f f f f e e e e f f f f . .
    . f f e f b f 4 4 f b f e f f .
    . f e e 4 1 f d d f 1 4 e e f .
    . . f e e d d d d d d e e f . .
    . . . f e e 4 4 4 4 e e f . . .
    . . e 4 f 2 2 2 2 2 2 f 4 e . .
    . . 4 d f 2 2 2 2 2 2 f d 4 . .
    . . 4 4 f 4 4 5 5 4 4 f 4 4 . .
    . . . . . f f f f f f . . . . .
    . . . . . f f . . f f . . . . .
    `,img`
    . . . . . . . . . . . . . . . .
    . . . . . . f f f f . . . . . .
    . . . . f f f 2 2 f f f . . . .
    . . . f f f 2 2 2 2 f f f . . .
    . . f f f e e e e e e f f f . .
    . . f e e 2 2 2 2 2 2 e f f . .
    . f f e 2 f f f f f f 2 e f f .
    . f f f f f e e e e f f f f f .
    . . f e f b f 4 4 f b f e f . .
    . . f e 4 1 f d d f 1 4 e f . .
    . . e f e 4 d d d d 4 e f . . .
    . . e 4 d d e 2 2 2 2 f e f . .
    . . . e d d e 2 2 2 2 f 4 e . .
    . . . . e e f 5 5 4 4 f . . . .
    . . . . . f f f f f f f . . . .
    . . . . . . . . . f f f . . . .
    `],
200,
character.rule(Predicate.MovingDown)
)
character.loopFrames(
thePlayer,
[img`
    . . . . f f f f f f . . . . . .
    . . . f 2 f e e e e f f . . . .
    . . f 2 2 2 f e e e e f f . . .
    . . f e e e e f f e e e f . . .
    . f e 2 2 2 2 e e f f f f . . .
    . f 2 e f f f f 2 2 2 e f . . .
    . f f f e e e f f f f f f f . .
    . f e e 4 4 f b e 4 4 e f f . .
    . . f e d d f 1 4 d 4 e e f . .
    . . . f d d d d 4 e e e f . . .
    . . . f e 4 4 4 e e f f . . . .
    . . . f 2 2 2 e d d 4 . . . . .
    . . . f 2 2 2 e d d e . . . . .
    . . . f 5 5 4 f e e f . . . . .
    . . . . f f f f f f . . . . . .
    . . . . . . f f f . . . . . . .
    `,img`
    . . . . . . . . . . . . . . . .
    . . . . f f f f f f . . . . . .
    . . . f 2 f e e e e f f . . . .
    . . f 2 2 2 f e e e e f f . . .
    . . f e e e e f f e e e f . . .
    . f e 2 2 2 2 e e f f f f . . .
    . f 2 e f f f f 2 2 2 e f . . .
    . f f f e e e f f f f f f f . .
    . f e e 4 4 f b e 4 4 e f f . .
    . . f e d d f 1 4 d 4 e e f . .
    . . . f d d d e e e e e f . . .
    . . . f e 4 e d d 4 f . . . . .
    . . . f 2 2 e d d e f . . . . .
    . . f f 5 5 f e e f f f . . . .
    . . f f f f f f f f f f . . . .
    . . . f f f . . . f f . . . . .
    `,img`
    . . . . f f f f f f . . . . . .
    . . . f 2 f e e e e f f . . . .
    . . f 2 2 2 f e e e e f f . . .
    . . f e e e e f f e e e f . . .
    . f e 2 2 2 2 e e f f f f . . .
    . f 2 e f f f f 2 2 2 e f . . .
    . f f f e e e f f f f f f f . .
    . f e e 4 4 f b e 4 4 e f f . .
    . . f e d d f 1 4 d 4 e e f . .
    . . . f d d d d 4 e e e f . . .
    . . . f e 4 4 4 e e f f . . . .
    . . . f 2 2 2 e d d 4 . . . . .
    . . . f 2 2 2 e d d e . . . . .
    . . . f 5 5 4 f e e f . . . . .
    . . . . f f f f f f . . . . . .
    . . . . . . f f f . . . . . . .
    `,img`
    . . . . . . . . . . . . . . . .
    . . . . f f f f f f . . . . . .
    . . . f 2 f e e e e f f . . . .
    . . f 2 2 2 f e e e e f f . . .
    . . f e e e e f f e e e f . . .
    . f e 2 2 2 2 e e f f f f . . .
    . f 2 e f f f f 2 2 2 e f . . .
    . f f f e e e f f f f f f f . .
    . f e e 4 4 f b e 4 4 e f f . .
    . . f e d d f 1 4 d 4 e e f . .
    . . . f d d d d 4 e e e f . . .
    . . . f e 4 4 4 e d d 4 . . . .
    . . . f 2 2 2 2 e d d e . . . .
    . . f f 5 5 4 4 f e e f . . . .
    . . f f f f f f f f f f . . . .
    . . . f f f . . . f f . . . . .
    `],
200,
character.rule(Predicate.MovingLeft)
)
character.loopFrames(
thePlayer,
[img`
    . . . . . . f f f f . . . . . .
    . . . . f f e e e e f f . . . .
    . . . f e e e f f e e e f . . .
    . . f f f f f 2 2 f f f f f . .
    . . f f e 2 e 2 2 e 2 e f f . .
    . . f e 2 f 2 f f 2 f 2 e f . .
    . . f f f 2 2 e e 2 2 f f f . .
    . f f e f 2 f e e f 2 f e f f .
    . f e e f f e e e e f e e e f .
    . . f e e e e e e e e e e f . .
    . . . f e e e e e e e e f . . .
    . . e 4 f f f f f f f f 4 e . .
    . . 4 d f 2 2 2 2 2 2 f d 4 . .
    . . 4 4 f 4 4 4 4 4 4 f 4 4 . .
    . . . . . f f f f f f . . . . .
    . . . . . f f . . f f . . . . .
    `,img`
    . . . . . . . . . . . . . . . .
    . . . . . . f f f f . . . . . .
    . . . . f f e e e e f f . . . .
    . . . f e e e f f e e e f . . .
    . . . f f f f 2 2 f f f f . . .
    . . f f e 2 e 2 2 e 2 e f f . .
    . . f e 2 f 2 f f f 2 f e f . .
    . . f f f 2 f e e 2 2 f f f . .
    . . f e 2 f f e e 2 f e e f . .
    . f f e f f e e e f e e e f f .
    . f f e e e e e e e e e e f f .
    . . . f e e e e e e e e f . . .
    . . . e f f f f f f f f 4 e . .
    . . . 4 f 2 2 2 2 2 e d d 4 . .
    . . . e f f f f f f e e 4 . . .
    . . . . f f f . . . . . . . . .
    `,img`
    . . . . . . f f f f . . . . . .
    . . . . f f e e e e f f . . . .
    . . . f e e e f f e e e f . . .
    . . f f f f f 2 2 f f f f f . .
    . . f f e 2 e 2 2 e 2 e f f . .
    . . f e 2 f 2 f f 2 f 2 e f . .
    . . f f f 2 2 e e 2 2 f f f . .
    . f f e f 2 f e e f 2 f e f f .
    . f e e f f e e e e f e e e f .
    . . f e e e e e e e e e e f . .
    . . . f e e e e e e e e f . . .
    . . e 4 f f f f f f f f 4 e . .
    . . 4 d f 2 2 2 2 2 2 f d 4 . .
    . . 4 4 f 4 4 4 4 4 4 f 4 4 . .
    . . . . . f f f f f f . . . . .
    . . . . . f f . . f f . . . . .
    `,img`
    . . . . . . . . . . . . . . . .
    . . . . . . f f f f . . . . . .
    . . . . f f e e e e f f . . . .
    . . . f e e e f f e e e f . . .
    . . . f f f f 2 2 f f f f . . .
    . . f f e 2 e 2 2 e 2 e f f . .
    . . f e f 2 f f f 2 f 2 e f . .
    . . f f f 2 2 e e f 2 f f f . .
    . . f e e f 2 e e f f 2 e f . .
    . f f e e e f e e e f f e f f .
    . f f e e e e e e e e e e f f .
    . . . f e e e e e e e e f . . .
    . . e 4 f f f f f f f f e . . .
    . . 4 d d e 2 2 2 2 2 f 4 . . .
    . . . 4 e e f f f f f f e . . .
    . . . . . . . . . f f f . . . .
    `],
200,
character.rule(Predicate.MovingUp)
)
controller.moveSprite(thePlayer)

```

```package
arcade-story=github:microsoft/arcade-character-animations
```