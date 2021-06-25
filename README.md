# arcade-character-animations

A MakeCode Arcade extension for creating rules that control when animations run on a sprite.

## Basic Rules

To attach animations to a sprite, you first need to create a "Rule" that dictates when the animation will run. Rules are made up of several parts that each describe a sprite's behavior. For example, if we were making a platformer here are some of the rules we might use to control the walking animations:

* Running Right: "Moving" + "Facing Right" + "Is Hitting Wall Down"
* Running Left: "Moving" + "Facing Left" + "Is Hitting Wall Down"

In this example, "Is Hitting Wall Down" is used to check if the sprite is on the ground or not.

If we wanted to add jumping to our sprite, we could create two more rules that look like this:

* Jumping Right: "Moving" + "Facing Right"
* Jumping Left: "Moving" + "Facing Left"

You might notice that one of the jumping rules will be true whenever the running rules are true. In this extension, the most specific rule will always override all of the others. So, if we have a sprite that is moving, facing right, and hitting a wall downwards, the running rule will run since it is more specific (it has three parts instead of two).

### Example: walking in four directions

This example shows how to make a simple top-down style game where you can walk in all four directions.

https://makecode.com/_AiHHa2WyoTbg

!()[./pngs/top-down.png]

One way you could extend this example is to add animations when the character is pushing up against a wall!


### Example: sidescrolling platformer

This example creates common animations that you might use in a platformer: running, jumping, and idling.

https://makecode.com/_Msz5ftemyYtU

!()[./pngs/platformer.png]

You could extend this example by adding different animations for when the player is jumping vs falling!


## Supported targets

* for PXT/arcade
* for PXT/arcade
(The metadata above is needed for package search.)

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft
trademarks or logos is subject to and must follow
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
