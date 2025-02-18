---
layout: archive
title: "Foundations of Multi-Agent Path Finding"
permalink: /research/mapf/
author_profile: true
---

{% include base_path %}

<img src="https://jiaoyangli.me/images/mapf-demo.gif" title="mapf demo" style="float:right;width:200pt;padding-left:10px;"  alt="mapf demo"/>
Recent advances in robotics have laid the foundation for building large-scale multi-agent systems. 
A great deal of research has focused on coordinating agents to fulfill different types of tasks. 
We focus on one fundamental task - 
to navigate teams of agents in a shared environment to their goal locations 
without colliding with obstacles or other agents.
One well-studied abstract model for this problem is known as **Multi-Agent Path Finding (MAPF)**. 
It is defined on a general graph with given start and goal vertices for agents on this graph. 
Each agent is allowed to wait at its current vertex or 
move to an adjacent vertex from one discrete timestep to the next one. 
We are asked to find a path for each agent such that no two agents are at the same vertex or 
cross the same edge at any timestep (because this would result in a collision). 
The objective is to minimize the sum of the arrival times of all agents.

We push the limits of MAPF solving by developing a variety of AI and optimization techniques to 
systematically reasoning about the **collision-resolution space** of the problem. 
Our optimal, bounded-suboptimal, and suboptimal MAPF algorithms can find solutions for 
a few hundred, a thousand, and a few thousand agents, respectively, within just a minute. 
The diagram below summarizes the empirical performance of some of our MAPF algorithms (solid lines)
in comparison to some baseline MAPF algorithms (dashed lines).
Success rate is the percentage of MAPF instances solved within a runtime limit of one minute.
<p style="text-align:center;">
<img src="https://jiaoyangli.me/images/benchmark.png" title="mapf demo" width="800pt" alt="benchmark"/>
</p>
<details>
    <summary>Show more details of this empirical result.</summary>
    The experiments were conducted on AWS EC2 instances “m4.large” with a runtime of 1 minute. 
    The MAPF instances are the 25 instances in the ``random'' scenario on map ``Paris_1_256'' 
    from <a href="https://movingai.com/benchmarks/mapf/index.html">the MAPF benchmark suite</a>. 
    The details of each MAPF algorithm are as follows.
    <ul>
    <li>
        A* is a vanilla A* algorithm that searches the joint-state space of the agents.
    </li>
    <li>
        CBS is from 
        <a href="https://ojs.aaai.org/index.php/AAAI/article/view/8140">[Sharon et al AAAI'12]</a>.
        Check out the code <a href="https://github.com/Jiaoyang-Li/CBSH2-RTC">here</a>.  
    </li>
    <li>
        ICBS is CBS with the conflict prioritization technique from 
        <a href="https://www.ijcai.org/Abstract/15/110">[Boyarski et al IJCAI'15]</a>.
        Check out the code <a href="https://github.com/Jiaoyang-Li/CBSH2-RTC">here</a>.  
    </li>
    <li>
        CBSH2-RTC is ICBS with 
        the WDG heuristic from <a href="https://jiaoyangli.me/publications/LiIJCAI19">our IJCAI'19 paper</a>, 
        the RTC symmetry reasoning from <a href="https://jiaoyangli.me/publications/LiAIJ21">our AIJ'21 paper</a>, and 
        the bypassing technique from <a href="https://www.ijcai.org/Abstract/15/110">[Boyarski et al IJCAI'15]</a>. 
        Check out the code <a href="https://github.com/Jiaoyang-Li/CBSH2-RTC">here</a>.  
    </li>
    <li>
        EECBS is the most advanced version of EECBS from 
        <a href="https://jiaoyangli.me/publications/LiAAAI21eecbs">our AAAI'21 paper</a> plus SIPPS from 
        <a href="https://jiaoyangli.me/publications/LiAAAI22">our AAAI'22 paper</a>.
        Check out the code <a href="https://github.com/Jiaoyang-Li/EECBS">here</a>.  
    </li>
    <li>
        PBS is PBS from <a href="https://jiaoyangli.me/publications/MaAAAI19">our AAAI'19 paper</a> 
        plus SIPPS from <a href="https://jiaoyangli.me/publications/LiAAAI22"> our AAAI'22 paper</a>.
        Check out the code <a href="https://github.com/Jiaoyang-Li/PBS">here</a>.  
    </li>
    <li>
        MAPF-LNS2 is from <a href="https://jiaoyangli.me/publications/LiAAAI22"> our AAAI'22 paper</a>. 
        Check out the code <a href="https://github.com/Jiaoyang-Li/MAPF-LNS2">here</a>.  
    </li>
    </ul>
    In terms of solution quality of suboptimal algorithms, PBS find very close-to-optimal solutions. 
    For instance, for 400 agents, PBS finds solutions 0.17% better than 
        EECBS(1.01) (which finds solutions provably at most 1% worse than optimal) on average. 
    For 800 agents, PBS finds solutions 0.31% better than EECBS(1.02) on average.
    MAPF-LNS2 finds close-to-optimal solutions. 
    For instance, for 2,500 agents, it finds solutions that are 32% worse than optimal on average.
    For 3,800 agents, it solves 2 instances with solutions 44% worse than optimal on average.

</details>

<!-- My research concentrates on developing AI techniques to bridge the gap between MAPF and real-world applications. My main contributions are summarized as follows: 
- Improving the scalability of MAPF algorithms:
  - Developing **symmetry reasoning** techniques to speed up optimal and bounded-suboptimal MAPF algorithms.
  - Introducing **heuristics** to conflict-based search to speed up optimal and bounded-suboptimal MAPF algorithms.
- Applying MAPF to various multi-agent systems:
  - Applying MAPF to **automated warehousing**.
  - Applying MAPF to **traffic management**.
  - Applying MAPF to multi-robot systems with **heterogeneous and nonholonomic robots**. -->


## Symmetry Reasoning for MAPF
<img src="https://jiaoyangli.me/images/rectangle.png" title="rectangle symmetry" style="float:left;width:250pt;padding-right:10px;"  alt="symmetry"/>
One of the reasons MAPF problems are so hard to solve is due to a phenomena called pairwise path symmetry, which occurs when two agents have many equivalent paths, all of which appear promising, but which are
pairwise incompatible because they result in a collision. 
The symmetry arises commonly in practice and can produce an exponential explosion in the space of possible collision resolutions, leading to unacceptable runtimes for currently state-of-the-art MAPF algorithms that employ heuristic search, such as Conflict-based Search (CBS).
To break symmetries, we propose a variety of constraint-based reasoning techniques, to detect the symmetries as they arise and to efficiently eliminate, in a single branching step, all permutations of two currently assigned but pairwise incompatible paths.     
 
Highlights: 
The addition of the symmetry-reasoning techniques proposed in [3] can 
reduce the number of expanded nodes and runtime of the optimal algorithm CBS by up to **4 orders of magnitude** and 
thus can handle up to **30 times more agents** than possible before within one minute.         

Relevant publications: 
[1] [rectangle symmetry](https://jiaoyangli.me/publications/LiAAAI19symmetry), 
[2] [corridor and target symmetries](https://jiaoyangli.me/publications/LiICAPS20), 
[3] [generalized rectangle, target, and corridor symmetry reasoning](https://jiaoyangli.me/publications/LiAIJ21), 
[4] [automatic symmetry reasoning by mutex propagation](https://jiaoyangli.me/publications/ZhangICAPS20) (**ICAPS'20 outstanding student paper**), 
[5] [mutex propagation for SAT-based MAPF](https://jiaoyangli.me/publications/SurynekPRIMA20), 
[6] [improved mutex propagation](https://jiaoyangli.me/publications/ZhangAIJ22),
[7] [symmetry reasoning for k-robust MAPF](https://jiaoyangli.me/publications/ChenAAAI21robust),
[8] [symmetry reasoning for agents of different shapes](https://jiaoyangli.me/publications/ZhangSoCS22),
[9] [symmetry reasoning for train-like agents](https://jiaoyangli.me/publications/ChenSoCS22), 
[10] [target symmetries used for MAPF with precedence constraints](https://jiaoyangli.me/publications/ZhangAAMAS22), and
[11] [symmetry reasoning with bounded-suboptimal CBS](https://jiaoyangli.me/publications/LiAAAI21eecbs).


## Heuristics for MAPF with Conflict-Based Search
<img src="https://jiaoyangli.me/images/heuristics.png" title="heuristic graph" style="float:left;width:250pt;padding-right:10px;" alt="heuristics"/>
Conflict-Based Search (CBS) and its enhancements are among the strongest algorithms for MAPF. 
However, existing variants of CBS do not use any heuristics that estimate future work.
Introducing admissible heuristics to guide the high-level search of CBS can significantly reduce the size of the CBS search tree and its runtime.
Introducing more informed but potentially inadmissible heuristics to guide the high-level search of bounded-suboptimal CBS with Explicit Estimation Search can further reduce the size of its search tree and its runtime.           

Highlights: 
The addition of the admissible heuristics proposed in [2] can 
reduce the number of expanded nodes and runtime of CBS by up to **a factor of 50** and 
thus can handle up to **3 times more agents** than possible before within one minute.
The bounded-suboptimal MAPF algorithm proposed in [4] can 
find solutions that are **provably at most 2% worse than optimal** with **1,000 agents** in one minute, 
while, on the same map, state-of-the-art optimal algorithms can handle at most 200 agents.             

Relevant publications: 
[1] [CG heuristic for CBS](https://jiaoyangli.me/publications/FelnerICAPS18), 
[2] [DG and WDG heuristics for CBS](https://jiaoyangli.me/publications/LiIJCAI19), 
[3] [generalized WDG heuristic for CBS with large agents](https://jiaoyangli.me/publications/LiAAAI19large), and
[3] [inadmissible heuristic for bounded-suboptimal CBS](https://jiaoyangli.me/publications/LiAAAI21eecbs).


## Large Neighborhood Search for MAPF
<img src="https://jiaoyangli.me/images/lns-framework.png" title="LNS framework" style="float:left;width:500pt;padding-right:10px;" alt="heuristics"/>
Sometimes, we are interested in a good solution but not necessarily a proof of how good the solution is. 
Since providing optimality proofs is computationally expensive, 
We develop Large Neighbor Search (LNS) algorithms 
that repeatedly replan paths for subsets of agents via prioritized planning. 
They give up optimality guarantees 
but find near-optimal solutions for thousands of agents in practice, 
solve 80% of the most challenging instances in the MAPF benchmark suite 
(while previously the best suboptimal algorithms solve at most 65%), and 
improve the solution quality by up to 36 times. 

Relevant publications: 
[1] [LNS for improving solution quality](https://jiaoyangli.me/publications/LiIJCAI21),
[2] [LNS for increasing success rates](https://jiaoyangli.me/publications/LiAAAI22),
[3] [LNS for railway planning and replanning](https://jiaoyangli.me/publications/ICAPS21),
[4] [machine learning guided LNS for MAPF](https://jiaoyangli.me/publications/HuangAAAI22), and
[5] [LNS for multi-agent task and path planning](https://jiaoyangli.me/publications/XuIROS22).

## Learning-Guided Planning
Machine Learning (ML) can complement the search algorithms and boost their performance 
by automatically discovering policies that are better than the hand-crafted ones and tailoring the randomized heuristics to the instances at hand.
Examples include learning to generate priority orderings for prioritized planning
and to select subsets of agents
and determine the stopping criterion for LNS. 

Relevant publications: 
[1] [ML-guided LNS for MAPF](/publications/HuangAAAI22), and
[2] [ML-guided prioritized planning for MAPF](/publications/ZhangSoCS22). 

## Learning individual policies for agents
An appealing alternative approach to using heuristic search methods is to use machine learning to directly learn a MAPF
policy for each agent. Depending on implementation, this could theoretically be 
decentralized (e.g. each agent running its own policy and communicating with a small subset of neighboring agents), 
fast (just the time required for a neural network inference), and 
result in efficient paths.

[1] [Imitation learning for MAPF](https://jiaoyangli.me/publications/VeerapaneniICRA25), and
[2] [Imitation learning for large-scale lifelong MAPF](/publications/JiangICRA25).

<div style="float: right;">
    <a href="https://jiaoyangli.me/research/"><strong>Back to the Research page</strong></a>
</div>

<!-- Other methods: hierarchical mapf, incremental CBS, flex distribution -->
