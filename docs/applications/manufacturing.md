---
layout: page
title: Manufacturing
permalink: /manufacturing/
published: True
---
On-orbit manufacturing offers an opportunity to create new structures which need not be designed to withstand the loads due to launch. Opportunities exist to advance techniques in decentralized multi-agent construction and novel manufacturing processes to take space manufacturing to new levels using our revolutionary concepts.

# Assembling Modular Structures Using Multiple Agents
Building large structures in space, like NASA's conceptual [Modular Active Self-Assembling Space Telescope](https://ntrs.nasa.gov/api/citations/20190018062/downloads/20190018062.pdf) or a space solar power station, will require maneuvering large numbers of modules in close proximity to each other and the structure being built. Planning paths for robots to do the assembly rapidly while avoiding collisions is an extremely challenging problem involving a very high dimensional state space and a very long planning horizon. We develop algorithms capable of rapidly producing high quality solutions to planning problems motivated by multi-agent construction to reveal the fundamental tools necessary for multi-agent assembly planning at scale.

Our first results showed that when it is possible to decompose a desired structure into smaller independent substructures, planning for each substructure separately then merging the resulting plans is effective at reducing planning time. These results were presented at [IROS2023](https://drive.google.com/file/d/1UYKnLZ1hnmD_WqzNmaUvs3alWWXI7BJc/view?usp=sharing). However, this "meta-algorithm" relies on another algorithm to actually plan for the substructures, and its performance is heavily dependent on the performance of the substructure planner.

In our follow-on work, we developed a hierarchical planning pipeline for a single structure. We first plan a feasible order by which a single agent could assemble the modules, then obtain low-level actions for multiple robots to achieve that assembly order. By abstracting part of the planning into an assembly order problem, the planning horizon is reduced dramatically.

![Schematic of the hierarchical planning pipeline. Given a goal structure, a sequence of abstracted actions by which a single agent could build the structure is found. Abstract actions that could occur simultaneously are identified and passed to a multi-agent path finding algorithm to construct the low-level multi agent plan to build the structure.](../assets/images/HierarchicalPlanning.png)


We achieve dramatic reductions in planning time using our developed algorithms, as compared to a [state of the art planner](https://doi.org/10.1007/978-3-030-58475-7_43) based on mixed integer-linear programming:
![Images of four structures, with tables reporting the solve time, makespan, and sum of costs for an existing optimization based planner, the decomposition approach, and the hierarchical planner. The optimization planner takes >10000 seconds for each structure, while the hierarchical planner solves each structure in less than 20 seconds.](../assets/images/MACCPerformanceSummary.png)