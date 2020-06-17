# Mir Visual Components Sim
Visual Components Simulation of MiR Robots

The files you want end on the `.vcmx` extension. You can ignore the ones with the `.bk` suffix in the backup directory.

The robot starts a bit off from the initial point A. If you move it closer so that it starts at A from a stationary position it'll have a little jiggle. Not really sure what's going on there but the timer can start when the robot reaches A anyway.

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

See below for the view in visual components.

![Alt text](Images/Components.png?raw=true "Components")

# Task Control

In order to get the MiR to move it needs to be directed using the Works Task Control component. You can do this by going clicking on Works Task Control, clicking the yellow open notes pop-up and going into the `Route Control::Orders` tab.

Honestly, the internal comments are pretty good. A route is defined using:
* A unique name. This needs to be assigned to an AVG in order to be used.
* A type. This specifies the behaviour of the AVG as it performs the route. There are three types:
  * Milk: Resource moves from task to task and of there is no task to be done, it will continue to next task (without waiting for event to trigger).
  * Force: Resource moves from task to task and processes all tasks. “Force” route will not activate until all tasks (like “feed’s and “need’s) are triggered.
  * Step: Resource moves from task to task and will wait for task to trigger
* Process: Name of the Works Process Component or “ANY” (in which case Resource will move to a component where event is triggered)
* Task: Type of the task. There are four:
  * Pick: Picks defined component (ProdID or ANY)
  * Place: Places defined components from resource (ProdID or ANY)
  * Move: Component name, moves to that component’s location (origin)
  * Wait: Resource will wait for X seconds (Process is not used and may e.g. "None")
* ID: ProdID value for a dynamic part to pick or place (like in Works) or Wait delay. Can be “ANY”  (pick any component from Process –component or place FIFO component from Resource matching any need. "ANY" can be used also with Move command)

As an example, one of the routes we've defined is:

```
#ROUTE NAME , TYPE , PROCESS:TASK:ID, PROCESS:TASK:ID 
moveAB,Milk,A:MOVE:ANY,B:MOVE:ANY
```

So the route name is moveAB, it's a Milk type of route (doesn't wait for any events), it fisrt moves to Process A, then to B. It doesn't do anything on arrival.




