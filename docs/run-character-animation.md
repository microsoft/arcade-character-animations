# run character animation

Adds an animation to a [sprite](/types/sprite) that will run whenever the given rule becomes true.
If there are multiple animations with rules that match a sprite's current state, the most specific rule will win.
If the given rule is invalid (e.g. "Moving and NotMoving") then the animation will be ignored.

This function is useful for animating when a sprite moves from one state to another.
For example, if a falling sprite lands on the ground you can run a landing animation before looping an idle animation.

```sig
characterAnimations.runFrames(
sprites.create(img`
    .
    `,
    [img`
    .
    `],
    500,
characterAnimations.rule(Predicate.NotMoving)
)
```

## Parameters

* **sprite**: a [sprite](/types/sprite) the sprite to run the animation on
* **animation**: the animation to run when the given rule becomes true
* **interval**: the number of milliseconds to spend on each frame of the animation before advancing to the next
* **rule**: a rule that controls when the animation will run on the sprite

## Example #example

In this example we animate a bug that jumps when you press the A button.
It has a jumping animation that runs when it starts moving up and a landing animation that runs when it stops moving.
Also note the looping idle animation that doesn't run until the landing animation is complete even though it has the same rule.

```blocks
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    jumper.ay = 500
    jumper.vy = -200
})
let jumper: Sprite = null
jumper = sprites.create(img`
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 1 6 1 6 . . . . .
    . . 6 . . 6 6 6 6 6 . . 6 . .
    . 6 . 6 . 6 6 6 6 6 . 6 . 6 .
    6 . . . 6 6 6 6 6 6 6 . . . 6
    `, SpriteKind.Player)
characterAnimations.runFrames(
jumper,
[img`
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 1 6 1 6 . . . . .
    . . 6 . . 6 6 6 6 6 . . 6 . .
    . 6 . 6 . 6 6 6 6 6 . 6 . 6 .
    6 . . . 6 6 6 6 6 6 6 . . . 6
    `,img`
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 1 6 1 6 . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . 6 6 . 6 6 6 6 6 . 6 6 . .
    . 6 . . 6 6 6 6 6 6 6 . . 6 .
    6 . . . . . . . . . . . . . 6
    `,img`
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 1 6 1 6 . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . 6 . 6 6 6 6 6 . 6 . . .
    . . 6 . 6 6 6 6 6 6 6 . 6 . .
    . 6 . . . . . . . . . . . 6 .
    6 . . . . . . . . . . . . . 6
    . . . . . . . . . . . . . . .
    `,img`
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 1 6 1 6 . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . 6 6 6 6 6 6 6 . . . .
    . . . 6 . . . . . . . 6 . . .
    . . . 6 . . . . . . . 6 . . .
    . . 6 . . . . . . . . . 6 . .
    . . 6 . . . . . . . . . 6 . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    `,img`
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 1 6 1 6 . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . 6 6 6 6 6 6 6 . . . .
    . . . . 6 . . . . . 6 . . . .
    . . . . 6 . . . . . 6 . . . .
    . . . 6 . . . . . . . 6 . . .
    . . . 6 . . . . . . . 6 . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    `],
25,
characterAnimations.rule(Predicate.MovingUp)
)
characterAnimations.runFrames(
jumper,
[img`
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 1 6 1 6 . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . 6 6 6 6 6 6 6 . . . .
    . . . . 6 . . . . . 6 . . . .
    . . . . 6 . . . . . 6 . . . .
    . . . 6 . . . . . . . 6 . . .
    . . . 6 . . . . . . . 6 . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    `,img`
    . . . . . . . . . . . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 1 6 1 6 . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . 6 6 6 6 6 6 6 . . . .
    . . . 6 . . . . . . . 6 . . .
    . . . 6 . . . . . . . 6 . . .
    . . 6 . . . . . . . . . 6 . .
    . . 6 . . . . . . . . . 6 . .
    . . . . . . . . . . . . . . .
    `,img`
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 1 6 1 6 . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . 6 . 6 6 6 6 6 . 6 . . .
    . . 6 . 6 6 6 6 6 6 6 . 6 . .
    . 6 . . . . . . . . . . . 6 .
    6 . . . . . . . . . . . . . 6
    `,img`
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 1 6 1 6 . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . 6 6 . 6 6 6 6 6 . 6 6 . .
    . 6 . . 6 6 6 6 6 6 6 . . 6 .
    6 . . . . . . . . . . . . . 6
    `,img`
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 1 6 1 6 . . . . .
    . . 6 . . 6 6 6 6 6 . . 6 . .
    . 6 . 6 . 6 6 6 6 6 . 6 . 6 .
    6 . . . 6 6 6 6 6 6 6 . . . 6
    `],
10,
characterAnimations.rule(Predicate.NotMoving)
)
characterAnimations.loopFrames(
jumper,
[img`
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 1 6 1 6 . . . . .
    . . 6 . . 6 6 6 6 6 . . 6 . .
    . 6 . 6 . 6 6 6 6 6 . 6 . 6 .
    6 . . . 6 6 6 6 6 6 6 . . . 6
    `,img`
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . . . . 6 1 6 1 6 . . . . .
    . . . . . 6 6 6 6 6 . . . . .
    . . 6 6 . 6 6 6 6 6 . 6 6 . .
    . 6 . . 6 6 6 6 6 6 6 . . 6 .
    6 . . . . . . . . . . . . . 6
    `],
500,
characterAnimations.rule(Predicate.NotMoving)
)
jumper.bottom = 120
game.onUpdate(function () {
    if (jumper.bottom > 120) {
        jumper.ay = 0
        jumper.vy = 0
        jumper.bottom = 120
    }
})

```

```package
arcade-story=github:microsoft/arcade-character-animations
```