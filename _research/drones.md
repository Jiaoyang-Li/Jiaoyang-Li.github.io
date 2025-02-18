---
layout: archive
title: "Planning for Complex Robot Teams"
permalink: /research/drones/
author_profile: true
---

{% include base_path %}
<img src="/images/mapf-app-framework.png" style="float:left;width:300pt;padding:10px;"  alt="Multi-Robot Coordination Framework"/>
Agents in MAPF are unrealistic and homogeneous, 
in the sense that each agent occupies exactly one vertex at any timestep and 
traverses exactly one edge or wait at its current vertex from one timestep to the next one. 
In the real world, however, robots might be of different shapes, have different kinematic constraints, and have different capabilities. We therefore aim to close the gap between the abstract agent models used by MAPF and the various complex robot models needed in the real world. 

<p style="text-align:center;">
    <img src="/images/mixed-robot-team.png" style="max-height:200pt" alt="mixed-robot-team"/>
</p>

## From Discrete Graphs and Timesteps to Continuous Space and Time
<div style="display: flex; flex-wrap: wrap; text-align: center">
    <div style="min-width:310px;flex: 1;margin: 5px;">
        <img src="/images/arena.gif" width="200px" alt="arena"/>
        <figcaption>Searching in a 2D space.</figcaption>
    </div>
    <div style="min-width:310px;flex: 1;margin: 5px;">
        <img src="/images/3Dmaze.gif" width="309px" alt="3D maze"/>
        <figcaption>Searching in a 3D space.</figcaption>
    </div>
    <div style="min-width:310px;flex: 1;margin: 5px;">
        <img src="/images/bar.gif" width="200px" alt="arm" />
        <figcaption>Searching in a high-dimensional space (i.e., configuration space).</figcaption>
    </div>
</div>
<div style="clear:both;"></div>

The agents in MAPF navigate on a general graph, which gives us the flexibility of applying MAPF algorithms to robots in 2D, 3D, and even higher-dimensional space, such as mobile robots, drones, and robotic arms. 
The challenge is how to build such graphs and connect the discretized MAPF world to the continuous real world.


Relevant publications: 
[1] [agents of different shapes](/publications/LiAAAI19large),
[2] [agents of nonholonomic dynamics](/publications/ChenAAAI21s2m2), 
[3] [time-robust plans](/publications/ChenAAAI21robust), 
[4] [snake-like agents](/publications/ChenSoCS22), and
[5] [motions planned by diffusion models](/publications/ShaoulICLR25).


## Moving in formation
<p style="text-align:center;">
    <img src="/images/formation-random-4x.gif" style="max-height:150pt" alt="formation-random"/>
    <img src="/images/formation-tight-4x.gif" style="max-height:150pt" alt="formation-tight"/>
    <img src="/images/formation-wide-4x.gif" style="max-height:150pt" alt="formation-wide"/>
</p>
Robots sometimes are required to move to their goal locations 
while maintaining a desired formation (i.e., spatial pattern), 
in order to reduce the system cost, increase the robustness and efficiency of the system. 

Relevant publications: 
[1] [agents that move in formation](https://jiaoyangli.me/publications/LiAAMAS20formation).

<div style="float: right;">
    <button onclick="location.href='https://jiaoyangli.me/research/'" type="button">Back to the Research page</button>
</div>