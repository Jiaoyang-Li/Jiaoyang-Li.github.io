---
permalink: /non-menu-page/
layout: archive
author_profile: true
redirect_from: 
  - "/nmp/"
  - "/nmp.html"
---
<!--title: "Page not in menu"
excerpt: "This is a page not in the main menu"-->
{% include base_path %}
<!--{% include toc %}-->

{% for pub in site.data.pubs %}
        {% include pub.html %}
{% endfor %}








<img src="/images/mapf-demo.gif" title="mapf demo" style="float:right;width:200pt;padding-left:10px;" />
Recent advances in robotics have laid the foundation for building large-scale multi-agent systems. 
However, how to coordinate the robots intelligently is a difficult problem because the joint-state space increases exponentially with the number of agents.
To tackle this challenge, I started with one fundamental problem called **Multi-Agent Path Finding (MAPF)**, which is to plan collision-free paths on a graph for a team of agents while minimizing their travel times.
My research concentrates on developing AI techniques to bridge the gap between MAPF and real-world applications. My main contributions are summarized as follows: 
- Improving the scalability of MAPF algorithms:
  - Developing **symmetry breaking** techniques to reduce the search space.
  - Introducing **informed heuristics** to conflict-based search to guide the search direction.
- Applying MAPF to various multi-agent systems:
  - Applying MAPF to **automated warehousing**.
  - Applying MAPF to **traffic management**.
  - Applying MAPF to multi-robot systems with **heterogeneous and nonholonomic robots**.

## Symmetry Breaking for MAPF
<img src="/images/rectangle.png" title="rectangle symmetry" style="float:left;width:200pt;padding-right:10px;" />
One of the reasons MAPF problems are so hard to solve is due to a phenomena called pairwise path symmetry, which occurs when two agents have many equivalent paths, all of which appear promising, but which are
pairwise incompatible because they result in a collision. 
The symmetry arises commonly in practice and can produce an exponential explosion in the space of possible collision resolutions, leading to unacceptable runtimes for currently state-of-the-art MAPF algorithms that employ heuristic search, such as Conflict-based Search (CBS).
To break symmetries, we propose a variety of constraint-based reasoning techniques, to detect the symmetries as they arise and to efficiently eliminate, in a single branching step, all permutations of two currently assigned but pairwise incompatible paths.     
 
Highlights: 
The addition of the symmetry-reasoning techniques proposed in [3] can reduce the number of expanded nodes and runtime of the optimal algorithm CBS by up to **4 orders of magnitude** and thus can handle up to **30 times more agents** than possible before within one minute.         

Relevant publications: 
[1] [rectangle symmetry](https://aaai.org/ojs/index.php/AAAI/article/view/4565 "AAAI 2019"), 
[2] [corridor and target symmetries](https://www.aaai.org/ojs/index.php/ICAPS/article/view/6661/6515 "ICAPS 2020"), 
[3] [generalized rectangle, target, and corridor symmetry reasoning](https://arxiv.org/abs/2103.07116 "Preprint 2021"), 
[4] [automatic symmetry reasoning by mutex propagation](https://www.aaai.org/ojs/index.php/ICAPS/article/view/6677/6531 "ICAPS 2020") (**ICAPS'20 outstanding student paper**), 
[5] [mutex propagation for SAT-based MAPF](https://jiaoyang-li.github.io/files/2020-PRIMA.pdf "PRIMA 2020"), 
[6] [symmetry reasoning for k-robust MAPF](https://jiaoyang-li.github.io/files/2021-AAAI-4.pdf "AAAI 2021"), and 
[7] [symmetry reasoning with bounded-suboptimal CBS](https://arxiv.org/abs/2010.01367 "AAAI 2021").


## Heuristics for MAPF with Conflict-Based Search
<img src="/images/heuristics.png" title="heuristic graph" style="float:left;width:250pt;padding-right:10px;" />
Conflict-Based Search (CBS) and its enhancements are among the strongest algorithms for MAPF. 
However, existing variants of CBS do not use any heuristics that estimate future work.
Introducing admissible heuristics to guide the high-level search of CBS can significantly reduce the size of the CBS search tree and its runtime.
Introducing more informed but potentially inadmissible heuristic to guide the high-level search of bounded-suboptimal CBS with Explicit Estimation Search can further reduce the size of its search tree and its runtime.           

Highlights: 
The addition of the admissible heuristics proposed in [2] 
can reduce the number of expanded nodes and runtime of CBS by up to **a factor of 50** 
and thus can handle up to **3 times more agents** than possible before within one minute.
The bounded-suboptimal MAPF algorithm proposed in [3] can find solutions 
that are **provably at most 2% worse than optimal** with **1,000 agents** in one minute, 
while, on the same map, state-of-the-art optimal algorithms can handle at most 200 agents.             

Relevant publications: 
[1] [CG heuristic for CBS](https://aaai.org/ocs/index.php/ICAPS/ICAPS18/paper/view/17735/16965 "ICAPS 2018"), 
[2] [DG and WDG heuristics for CBS](https://www.ijcai.org/proceedings/2019/0063.pdf "IJCAI 2019"), and
[3] [inadmissible heuristic for bounded-suboptimal CBS](https://arxiv.org/abs/2010.01367 "AAAI 2021").


## Lifelong MAPF for Automated Warehousing
<!--
<img src="https://jiaoyang-li.github.io/images/PBS_w=10_800agents-8x.mp4" title="warehouse demo" style="float:left;width:250pt;padding-right:10px;" />
<figure class="video_container">
  <video width="320" autoplay loop>
    <source src="https://jiaoyang-li.github.io/images/Single+_800agents-8x.mp4" type="video/mp4">
    <source src="https://jiaoyang-li.github.io/images/PBS_w=10_800agents-8x.mp4" type="video/mp4">
  </video>
</figure>
<video width="320" height="240" controls>
  <source src="https://jiaoyang-li.github.io/images/warehouse.mkv" type="video/mkv">
</video>
--> 



 <div id="wrapper" align="center" style="float:left;width:250pt;padding-right:10px;"> 
     <video id="single-agent" width="250pt"  autoplay loop controls> 
         <source type="video/mp4" src="https://jiaoyang-li.github.io/images/Single+_800agents-8x.mp4" /> 
     </video>
    <figcaption>Traditional single-agent solver</figcaption>
     <video id="multi-agent" width="250pt"  autoplay loop controls> 
         <source type="video/mp4" src="https://jiaoyang-li.github.io/images/PBS_w=10_800agents-8x.mp4" /> 
     </video>
     <figcaption>Our MAPF solver</figcaption>
     <div class="clear"></div> 
 </div>
Today, in automated warehouses, mobile robots already autonomously move inventory pods or flat packages from one location to another. Finding low-cost paths for the robots in real-time is essential for the effectiveness of such systems. However, MAPF is only the “one-shot” variant of the actual problem in many applications. Typically, after an agent reaches its goal location, it does not stop and wait there forever. Instead, it is assigned a new goal location and required to keep moving, which is referred to as lifelong MAPF and characterized by agents constantly being assigned new goal locations. 
There are two challenges in this problem, namely how to assign tasks to agents and how to decompose the lifelong problem to one-shot MAPF problems.               

Highlights:
The RHCR algorithm proposed in [3] can produce high-quality solutions for **1,000 agents** (= **38.9% of the empty cells** on the map) for simulated warehouse instances. The left videos show the performance of 800 agents on the same map with traditional single-agent solver and RHCR.

Relevant publications: 
[1] [MAPF with online task assignment](https://dl.acm.org/citation.cfm?id=3091243 "AAMAS 2017"), 
[2] [MAPF with offline task assignment](http://www.ifaamas.org/Proceedings/aamas2019/pdfs/p1152.pdf "AAMAS 2019"), 
[3] [rolling-horizon collision resolution](https://arxiv.org/abs/2005.07371 "AAAI 2021"), and
[4] [column generation for tasks with time windows](https://arxiv.org/abs/2103.08835 "Preprint 2021").

## MAPF for Traffic Management
<img src="/images/flatland.gif" title="flatland demo" style="float:left;width:250pt;padding-right:10px;" />

MAPF can also be used for traffic management for autonomous vehicle, trains, or airplanes. This can reduce traffic congestion, energy consumption, and air pollution. The main challenges of applying MAPF to traffic management systems are two-fold. First, the systems are neither perfect nor deterministic. For example, the environment might cause unexpected disturbances, the communication network might not be stable, the agents might have incomplete knowledge of the environment, and the agents might not be able to execute their deterministic MAPF plans perfectly. We need to take such uncertainties into account during path planning and generate robust plans. Second, the system needs to operate thousands of (or even more) agents in real-time, so extremely efficient MAPF algorithms are required.          

Highlights:
The MAPF-based software we developed for the NeurIPS'20 Flatland Challenge in [1] can plan collision-free paths for **more than 3000 agents** within a few minutes and
deliver deadlock-free actions **in real-time** during execution that are robust to unexpected delays. It outperformed all other solutions, including all reinforcement learning solutions, to **win the overall first place** in both rounds. A comparison of our solution with top reinforcement learning solutions can be found in [2].

Relevant publications: 
[1] [railway planing and replanning](https://jiaoyangli.me/files/2021-ICAPS.pdf "ICAPS 2021") (**winner of the NeurIPS'20 Flatland Challenge**),
[2] [railway planing and replanning with MAPF and MARL](http://proceedings.mlr.press/v133/laurent21a.html), and
[3] [airport taxiway planning](https://arc.aiaa.org/doi/abs/10.2514/6.2019-2930 "AIAA 2019").         

## MAPF for Heterogeneous and Nonholonomic Robots
<div id="wrapper" align="center" style="float:left;width:150pt;padding-right:10px;"> 
  <img src="/images/arena.gif" title="mobile robots" style="width:250pt" />
  <figcaption>Mobile robot team</figcaption>
  <img src="/images/bar.gif" title="robotic arms" style="width:250pt" />
  <figcaption>Multi-arm assembly</figcaption>
</div>
Agents in MAPF are unrealistic and homogeneous, in the sense that each agent occupies exactly one vertex at any timestep and traverses exactly one edge or wait at its current vertex from one timestep to the next one. In the real world, however, agents might be of different shapes and have different kinematic constraints. Moreover, agents sometimes are required to move to their goal locations while maintaining a desired formation (i.e., spatial pattern), in order to reduce the system cost, increase the robustness and efficiency of the system. Notably, in addition to the traditional mobile robots/drones that navigate in a 2D/3D space, MAPF can be also used for planning trajectories for robotic arms! See the demo on the left (the work is under review at RAL/ICRA2022).


Relevant publications: 
[1] [agents of different shapes](https://aaai.org/ojs/index.php/AAAI/article/view/4756 "AAAI 2019"), 
[2] [agents of high-dimensional, nonlinear, and nonholonomic dynamics](https://ojs.aaai.org/index.php/AAAI/article/view/17340 "AAAI 2021"), and
[3] [agents that move in formation](http://ifaamas.org/Proceedings/aamas2020/pdfs/p726.pdf "AAMAS 2020").
