# matches rule

Checks the state of a sprite and returns true if it currently fulfills the given rule.

A sprite will not match any "Facing" rule unless it has at least one animation that uses that rule.

```sig
characterAnimations.matchesRule(sprites.create(img`
    .
    `, characterAnimations.rule(Predicate.NotMoving))
```

## Parameters

* **sprite**: a [sprite](/types/sprite) to check the state of
* **rule**: a rule to validate against the state of the sprite

## Example #example

This example checks to see if the player is facing left or right in the A button event so that the projectiles fire in the correct direction.

```blocks
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    if (characterAnimations.matchesRule(thePlayer, characterAnimations.rule(Predicate.FacingLeft))) {
        projectile = sprites.createProjectileFromSprite(img`
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . c b a c . . . . . .
            . . . . c c b c f a c . . . . .
            . . . . a f b b b a c . . . . .
            . . . . a f f b a f c c . . . .
            . . . . c b b a f f c . . . . .
            . . . . . b b a f a . . . . . .
            . . . . . . c b b . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            `, thePlayer, -100, 0)
    } else {
        projectile = sprites.createProjectileFromSprite(img`
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . c b a c . . . . . .
            . . . . c c b c f a c . . . . .
            . . . . a f b b b a c . . . . .
            . . . . a f f b a f c c . . . .
            . . . . c b b a f f c . . . . .
            . . . . . b b a f a . . . . . .
            . . . . . . c b b . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            `, thePlayer, 100, 0)
    }
})
let projectile: Sprite = null
let thePlayer: Sprite = null
scene.setBackgroundColor(11)
thePlayer = sprites.create(img`
    . . . . . . . . . . . .
    . . . f f f f f f . . .
    . f f f e e e e e f . .
    f f f e e e e e e e f .
    f f f f e e e e e e e f
    f f f f f e e e 4 e e f
    f f f f e e e 4 4 e e f
    f f f f 4 4 4 4 4 e f f
    f f 4 e 4 f f 4 4 e f .
    f f 4 d 4 d d d d f . .
    . f f f 4 d d b b f . .
    . 4 d d e 4 4 4 e f . .
    . e d d e 1 1 1 1 f . .
    . f e e f 6 6 6 6 f f .
    . f f f f f f f f f f .
    . . f f . . . f f f . .
    `, SpriteKind.Player)
characterAnimations.loopFrames(
thePlayer,
[img`
    . . . . . . . . . . . .
    . . . f f f f f f . . .
    . f f f e e e e e f . .
    f f f e e e e e e e f .
    f f f f e e e e e e e f
    f f f f f e e e 4 e e f
    f f f f e e e 4 4 e e f
    f f f f 4 4 4 4 4 e f f
    f f 4 e 4 f f 4 4 e f .
    f f 4 d 4 d d d d f . .
    . f f f 4 d d b b f . .
    . 4 d d e 4 4 4 e f . .
    . e d d e 1 1 1 1 f . .
    . f e e f 6 6 6 6 f f .
    . f f f f f f f f f f .
    . . f f . . . f f f . .
    `,img`
    . . . . . . . . . . . .
    . . . f f f f f f . . .
    . f f f e e e e e f . .
    f f f e e e e e e e f .
    f f f f e e e e e e e f
    f f f f f e e e 4 e e f
    f f f f e e e 4 4 e e f
    f f f f 4 4 4 4 4 e f f
    f f 4 e 4 f f 4 4 e f .
    . f 4 d 4 d d d d f . .
    . f f f e e d b b f . .
    . . f 4 d d e 4 e f . .
    . . f e d d e 1 1 f . .
    . f f f e e f 6 6 f f .
    . f f f f f f f f f f .
    . . f f . . . f f f . .
    `,img`
    . . . . f f f f f . . .
    . . f f e e e e e f . .
    . f f e e e e e e e f .
    f f f f e e e e e e e f
    f f f f f e e e 4 e e f
    f f f f e e e 4 4 e e f
    f f f f 4 4 4 4 4 e f f
    f f 4 e 4 f f 4 4 e f f
    . f 4 d 4 d d d d f f .
    . f f f 4 d d b b f . .
    . . f e e 4 4 4 e f . .
    . . 4 d d e 1 1 1 f . .
    . . e d d e 1 1 1 f . .
    . . f e e f 6 6 6 f . .
    . . . f f f f f f . . .
    . . . . f f f . . . . .
    `],
100,
characterAnimations.rule(Predicate.FacingRight)
)
characterAnimations.loopFrames(
thePlayer,
[img`
    . . . . . . . . . . . .
    . . . f f f f f f . . .
    . . f e e e e e f f f .
    . f e e e e e e e f f f
    f e e e e e e e f f f f
    f e e 4 e e e f f f f f
    f e e 4 4 e e e f f f f
    f f e 4 4 4 4 4 f f f f
    . f e 4 4 f f 4 e 4 f f
    . . f d d d d 4 d 4 f f
    . . f b b d d 4 f f f .
    . . f e 4 4 4 e d d 4 .
    . . f 1 1 1 1 e d d e .
    . f f 6 6 6 6 f e e f .
    . f f f f f f f f f f .
    . . f f f . . . f f . .
    `,img`
    . . . . . . . . . . . .
    . . . f f f f f f . . .
    . . f e e e e e f f f .
    . f e e e e e e e f f f
    f e e e e e e e f f f f
    f e e 4 e e e f f f f f
    f e e 4 4 e e e f f f f
    f f e 4 4 4 4 4 f f f f
    . f e 4 4 f f 4 e 4 f f
    . . f d d d d 4 d 4 f .
    . . f b b d e e f f f .
    . . f e 4 e d d 4 f . .
    . . f 1 1 e d d e f . .
    . f f 6 6 f e e f f f .
    . f f f f f f f f f f .
    . . f f f . . . f f . .
    `,img`
    . . . f f f f f . . . .
    . . f e e e e e f f . .
    . f e e e e e e e f f .
    f e e e e e e e f f f f
    f e e 4 e e e f f f f f
    f e e 4 4 e e e f f f f
    f f e 4 4 4 4 4 f f f f
    f f e 4 4 f f 4 e 4 f f
    . f f d d d d 4 d 4 f .
    . . f b b d d 4 f f f .
    . . f e 4 4 4 e e f . .
    . . f 1 1 1 e d d 4 . .
    . . f 1 1 1 e d d e . .
    . . f 6 6 6 f e e f . .
    . . . f f f f f f . . .
    . . . . . f f f . . . .
    `],
100,
characterAnimations.rule(Predicate.FacingLeft)
)
controller.moveSprite(thePlayer)

```

```package
arcade-character-animations=github:microsoft/arcade-character-animations
```