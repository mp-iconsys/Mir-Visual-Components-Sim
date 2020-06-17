# Mir Visual Components Sim
Visual Components Simulation of MiR Robots

The files you want end on the `.vcmx` extension. You can ignore the ones with the `.bk` suffix in the backup directory.

The robot starts a bit off from the initial point A. If you move it closer so that it starts at A from a stationary position it'll go a little jiggle. Not really sure what's going in there but the timer can start when the robot reaches A anyway.

# Guides & Documentation

A couple of useful guides: 

* [Youtube Video #1](https://www.youtube.com/watch?v=Tv_U-MA6mEQ)
* [Youtube Video #2](https://www.youtube.com/watch?v=4yT7kY3W0mU)

They have a fairly good breakdown so you don't need to trudge through all of it.

# Setting Up Components

Alright, so you actually only need a handful of components to get MiRs to move:
1. A Works Pathway Area big enough to contain the robot and all of its destinations
1. Works Processes. These can do things (create objects and feed them to the MiR) or they can exist as destinations between which to move.
1. Works Resource Pathfinder. This can just sit there and look pretty.
1. Works Task Control. This is where we'll program what the robot has to do.
1. A MiR so we've got an AVG that moves.


# Task Control

In order to get the MiR to move it needs to be directed using the Works Task Control component. You can do this by going clicking on Works Task Control, clicking the yellow open notes pop-up and going into the `Route Control::Orders` tab.






