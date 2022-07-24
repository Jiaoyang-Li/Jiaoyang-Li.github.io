---
layout: archive
title: "Coordination of Large Robot Teams in Automated Warehouses"
permalink: /research/warehouse/
author_profile: true
---

{% include base_path %}

<div style="display: flex; flex-wrap: wrap; text-align: center">
    <video style="min-width:300px;flex: 1;margin: 5px;"  autoplay loop controls> 
        <source type="video/mp4" src="https://jiaoyangli.me/images/Single+_800agents-8x.mp4" /> 
    </video>
    <figcaption>Traditional single-agent solver for automated warehouses</figcaption>
</div>
<div style="display: flex; flex-wrap: wrap; text-align: center">
    <video style="min-width:300px;flex: 1;margin: 5px;"  autoplay loop controls> 
        <source type="video/mp4" src="https://jiaoyangli.me/images/PBS_w=10_800agents-8x.mp4" /> 
    </video>
    <figcaption>Our MAPF solver for automated warehouses</figcaption>
</div>
<div style="clear:both;"></div>

Today, in automated warehouses, 
mobile robots already autonomously move inventory pods or flat packages from one location to another. 
Finding low-cost paths for the robots in real-time is essential for the effectiveness of such systems. 
However, MAPF is only the “one-shot” variant of the actual problem in many applications. 
Typically, after an agent reaches its goal location, it does not stop and wait there forever. 
Instead, it is assigned a new goal location and required to keep moving, 
which is referred to as lifelong MAPF and characterized by agents constantly being assigned new goal locations. 
There are three challenges in this problem, namely 
how to assign tasks to agents, 
how to decompose the lifelong problem to one-shot MAPF problems and solve it efficiently, and
how to handle robot dynamics and uncertainties during execution.


## Combined Task and Path Planning

Automated warehousing systems need to continually assign delivery tasks and collision-free paths to robots 
in an online manner. Traditional task assignment algorithms ignore collisions among agents, 
which can generate task assignments that eventually lead to costly collision-free paths or even no collision-free paths.
We develop various of combined task and path planning algorithms with different properties 
(e.g., optimal, complete, capable of handling time-window constraints, etc.) that suit for different scenarios.

Relevant publications: 
[1] [Decoupled online task assignment and path planning](https://jiaoyangli.me/publications/MaAAMAS17), 
[2] [Decoupled offline task assignment and path planning](https://jiaoyangli.me/publications/LiuAAMAS19), 
[3] [CBS-based optimal task and path planning](https://jiaoyangli.me/publications/ZhongICRA22), 
[4] [LNS-based task and path planning](https://jiaoyangli.me/publications/XuIROS22),
[5] [Deadline-aware task and path planning](https://jiaoyangli.me/publications/HuangHSI22), and
[6] [column generation for tasks with time windows](https://arxiv.org/abs/2103.08835 "Preprint 2021").


## Scalability and Solution Quality

<img src="https://jiaoyangli.me/images/single-vs-mapf.png" style="float:left;width:250pt;padding:10px;"  alt="Single vs MAPF"/>
The principled way of solving this challenge is to develop efficient and effective MAPF algorithms. 
More details can be found in our research on [Foundations of MAPF](https://jiaoyangli.me/research/mapf/).

Additionally, MAPF is only the “one-shot” variant of the actual problem in the automated warehouses. 
Typically, after an agent reaches its goal location, it does not stop and wait there forever, 
which requires us to call MAPF solvers periodically to plan and replan in an online manner.
This is a challenge but also an important property that we can make use of when we develop MAPF algorithms.

Highlights:
The RHCR algorithm proposed in [1] can produce high-quality solutions for **1,000 agents** (= **38.9% of the empty cells** on the map) for simulated warehouse instances. 
The videos shown at the top of the page 
show the performance of 800 agents on the same map with traditional single-agent solver and RHCR, and 
the figure on the left summarizes the throughput results with different numbers of agents.

Relevant publications: 
[1] [rolling-horizon collision resolution](https://jiaoyangli.me/publications/LiAAAI21lifelong).


## Combined Planning and Execution


<img src="https://jiaoyangli.me/images/warehouse-5x.gif" style="float:left;width:200pt;padding:10px;"  alt="warehouse"/>
MAPF algorithms can find high-quality collision-free plans for automated warehousing 
under simplified assumptions about the robot dynamics. 
However, these simplifying assumptions pose challenging implementational issues 
since the robots cannot follow the plans precisely. 
Therefore, some recent  research  has  focused  on  more  complicated MAPF models to close the gap.
But, robot dynamics are complex and almost impossible to be modeled perfectly.
We therefore study how  to combine (task and path) planning with execution control from two perspectives,
namely what planning model works best in terms of maximizing final throughput and minimizing planning time, and
how we overlap planning and execution to avoid robot idle time during replanning.

Relevant publications: 
[1] [Different MAPF models for warehouse robots](https://jiaoyangli.me/publications/VaramballySoCS22).


<div style="float: right;">
    <button onclick="location.href='https://jiaoyangli.me/research/'" type="button">Back to the Research page</button>
</div>
