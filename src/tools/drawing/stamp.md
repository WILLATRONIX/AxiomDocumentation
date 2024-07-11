# Stamp

The **Stamp Tool** is a [Blueprint](/editor/windows/blueprints.md) placement tool designed for placing muliple, randomly placed blueprints. Listed below are all [Tool Options](/editor/windows/tooloptions.md) for the **Stamp Tool**.

| Option                      | Description                                                                                                                                                                                                                                                                                                    |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Base Chance                 | The base chance is the final factor that determines placement. A base chance of 1 means it will always place the blueprint regarding the Min Spacing.                                                                                                                                                          |
| Min Spacing                 | The Minimum Spacing is the first factor that determines placement. A minimum spacing of 5 will result in the centre of two blueprints being at least five blocks apart.                                                                                                                                        |
| Place (Immediate)           | The immediate option places all blueprints immediately after releasing your brush stroke.                                                                                                                                                                                                                      |
| Place (Deferred)            | The deferred option allows you to place blueprints with multiple strokes. You can also manually offset and rotate the blueprints by using the [Gizmo](/editor/gizmos.md) located at the centre of the blueprint. New brush strokes will still apply the placement rules to previously placed blueprints.       |
| Random Yaw                  | Randomises the placement by rotating the blueprint in a random direction.                                                                                                                                                                                                                                      |
| Random X/Z Flip             | Randomises the placement by flipping the blueprint on the X and Z axis.                                                                                                                                                                                                                                        |
| Keep Existing               | When enabled, pre-existing blocks are not overridden.                                                                                                                                                                                                                                                          |
| Extend Foundation To Ground | If the bottom surface doesn't reach the ground, it will be duplicated down until it does.                                                                                                                                                                                                                      |

To load blueprints into the **Stamp Tool**, click the 'Add Blueprint' button. This will open your [Blueprint Browser](/editor/windows/blueprints.md#Blueprint_Browser) and click on the blueprint you'd like to add. To add multiple blueprints, you can either [Dock](/editor/windows/intro.md#Docking) the Blueprint Browser or use Shift + Click to avoid closing the window.

Blueprints have their own offset and chance. If the Base of your blueprint should be lower, you can edit it here. If you want less or more of a specific blueprint, you can also change that here. 

## Video Demo

<iframe width="560" height="315" src="https://www.youtube.com/embed/Vf4urSRSkdw?si=BQsjUDd7ZMWs4oNV" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>