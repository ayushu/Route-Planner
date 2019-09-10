# Route Planner Using A* Search

This project was done as part of the [Udacity Self-Driving Car Nanodegree](http://www.udacity.com/drive)

---

The goal of the project was to build a route-planning algorithm to calculate the shortest path between two points on a map.
The A* search algorithm was applied in Python using the straight-line distance to the goal as a heuristic function.

---  

## Helpers.py

The helpers.py file imports the necessary library for the the algorithm, namely pickle, plotly, and networkx. It also defines the Map class, and its associated functions which allow the map to be visualized. Finally, it also contains the two maps itself, one being used as a test map with only 10 intersections and also the main map which has 40 intersections. The final algorithm is applied to the main map.

## Map and Intersections

The map contains a network of the intersections, which are represented as a dictionary, each identified by an x,y coordinate. The roads, which are respresented as a list, detail the list if intersections that the given intersection connects to. For example, if Intersection 0 connects to Intersections 7, 6, and 5, then `map.road[0]` will be `[7, 6, 5]`.

The `show_map` function is used to visualize the map. The main map is shown below:

[Main Map](./images/full_map.png)

## Route Planning

The `PathPlanner` class is initialized with a map using `__init__`. From there, the following functions are used to implement A* search:
*`closedSet` includes any explored/visited nodes.
*`openSet` are any nodes on otheur frontier for potential future exploration.
*`cameFrom` will hold the previous node that best reaches a given node.
*`gScore` is the `g` in the `f = g + h` equation, or the actual cost to reach the current node.
*`fScore` is the combination of `g` and `h`, i.e. the `gScore` plus a heuristic; total cost to reach the goal.
*`path` comes from the `run_search` function.
*`is_open_empty` checks if there are still nodes to explore.
*`_reset` resets most of the initialized variables for the `PathPlanner` class.

Finally, the `run_search` and `reconstruct_path` functions run the required parts of the algorithm to find the shortest path from the origin to the destination.

The final output, using Intersection 5 as the origin, and Intersection 34 as the destination is shown below:

[Output Map](./images/map_routed.png)