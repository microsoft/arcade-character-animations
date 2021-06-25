# set character animations enabled

Enables or disables all animations with rules on a given [sprite](/types/sprite).
This function is useful if you want to temporarily run a normal animation on a sprite without it being overridden by another animation.

```sig
characterAnimations.setCharacterAnimationsEnabled(sprites.create(img`
    .
    `, true)
```

## Parameters

* **sprite**: a [sprite](/types/sprite) to set character animations enabled on
* **enabled**: a [boolean](/types/boolean) indicating whether the character animations are enabled or not

## Example #example

In this example, we create a character and an enemy sprite. When the character overlaps with the enemy, we bump them away and temporarily disable the character animations so that we can show a different animation while they are temporarily invincible. We then re-enable the character animations along with overlap events and controls for the sprite.

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) {
    characterAnimations.setCharacterAnimationsEnabled(sprite, false)
    animation.runImageAnimation(
    sprite,
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
        . . . . . . 2 2 2 2 . . . . . .
        . . . . 2 2 2 f f 2 2 2 . . . .
        . . . 2 2 2 f f f f 2 2 2 . . .
        . . 2 2 2 f f f f f f 2 2 2 . .
        . . 2 2 f f f f f f f f f 2 . .
        . . 2 f f 2 2 2 2 2 2 f f 2 . .
        . . 2 2 2 2 f f f f 2 2 2 2 . .
        . 2 2 f 2 f 2 f f 2 f 2 f 2 2 .
        . 2 f f f f 2 f f 2 f f f f 2 .
        . . 2 f f f f f f f f f f 2 . .
        . . . 2 f f f f f f f f 2 . . .
        . . f f 2 f f f f f f 2 f f . .
        . . f f 2 f f f f f f 2 f f . .
        . . f f 2 f f f f f f 2 f f . .
        . . . . . 2 2 2 2 2 2 . . . . .
        . . . . . 2 2 . . 2 2 . . . . .
        `],
    100,
    true
    )
    sprite.setFlag(SpriteFlag.GhostThroughSprites, true)
    angle = Math.atan2(sprite.y - otherSprite.y, sprite.x - otherSprite.x)
    controller.moveSprite(sprite, 0, 0)
    sprite.setVelocity(60 * Math.cos(angle), 60 * Math.sin(angle))
    pause(400)
    sprite.setVelocity(0, 0)
    animation.stopAnimation(animation.AnimationTypes.All, sprite)
    controller.moveSprite(sprite)
    sprite.setFlag(SpriteFlag.GhostThroughSprites, false)
    characterAnimations.setCharacterAnimationsEnabled(sprite, true)
})
let angle = 0
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
characterAnimations.loopFrames(
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
    `],
500,
characterAnimations.rule(Predicate.MovingRight)
)
characterAnimations.loopFrames(
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
    `],
500,
characterAnimations.rule(Predicate.MovingDown)
)
characterAnimations.loopFrames(
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
    `],
500,
characterAnimations.rule(Predicate.MovingLeft)
)
characterAnimations.loopFrames(
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
    `],
500,
characterAnimations.rule(Predicate.MovingUp)
)
controller.moveSprite(thePlayer)
let mySprite2 = sprites.create(img`
    . . . . c c c c c c . . . . . .
    . . . c 6 7 7 7 7 6 c . . . . .
    . . c 7 7 7 7 7 7 7 7 c . . . .
    . c 6 7 7 7 7 7 7 7 7 6 c . . .
    . c 7 c 6 6 6 6 c 7 7 7 c . . .
    . f 7 6 f 6 6 f 6 7 7 7 f . . .
    . f 7 7 7 7 7 7 7 7 7 7 f . . .
    . . f 7 7 7 7 6 c 7 7 6 f c . .
    . . . f c c c c 7 7 6 f 7 7 c .
    . . c 7 2 7 7 7 6 c f 7 7 7 7 c
    . c 7 7 2 7 7 c f c 6 7 7 6 c c
    c 1 1 1 1 7 6 f c c 6 6 6 c . .
    f 1 1 1 1 1 6 6 c 6 6 6 6 f . .
    f 6 1 1 1 1 1 6 6 6 6 6 c f . .
    . f 6 1 1 1 1 1 1 6 6 6 f . . .
    . . c c c c c c c c c f . . . .
    `, SpriteKind.Enemy)

```

```package
arcade-story=github:microsoft/arcade-character-animations
```