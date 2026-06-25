# RelAfford6D: Relational 6D Affordance Graphs for Constraint-Driven Robotic Manipulation

<p align="center">
  <a href="#">Paper</a> |
  <a href="#">Project Page</a> |
  <a href="#">Code</a> |
  <a href="#">Video</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/ECCV-2026-blue" alt="ECCV 2026">
  <img src="https://img.shields.io/badge/Task-Robotic%20Manipulation-green" alt="Robotic Manipulation">
  <img src="https://img.shields.io/badge/Code-Coming%20Soon-lightgrey" alt="Code Coming Soon">
</p>

<p align="center">
  Guodong Zhang, Qichen He, Wenyuan Xie, Shaokai Wu, Yanbiao Ji, Qiuchang Li, Bayram Bayramli, Yue Ding, Hongtao Lu
  <br>
  School of Computer Science, Shanghai Jiao Tong University
</p>

## Overview

RelAfford6D is a training-free framework for open-world robotic manipulation. The key idea is to represent manipulation as a relational 6D affordance graph, where a primary interacting part is explicitly linked to its physical anchor. This relation is then elevated into metric `SE(3)` poses and executed through closed-loop kinematic constraint tracking.

Instead of predicting isolated contact points or learning an end-to-end policy, RelAfford6D uses structured semantic topology, vision foundation models, and analytic constraint-driven execution to generate physically valid manipulation trajectories for articulated and rigid objects.

<p align="center">
  <img src="./fig1.png" width="95%" alt="RelAfford6D overview">
</p>

## Method

RelAfford6D consists of three stages:

1. **Semantic Topology Generation**  
   A structured kinematic knowledge base and retrieval-augmented LLM reasoning infer the manipulated object, the primary interacting part, the physical anchor, and the action relation.

2. **Metric Visual Grounding**  
   Vision foundation models ground the inferred parts in RGB-D observations and estimate part-level 6D poses. In the camera-ready version, we use the model-free FoundationPose pipeline with object-specific meshes reconstructed from RGB-D reference views.

3. **Constraint-Driven Kinematic Execution**  
   The relational part poses define revolute, prismatic, or rigid-body constraint manifolds. The robot tracks these manifolds in closed loop and replans online when the object state changes.

## Experiments

We evaluate RelAfford6D in simulation and real-world settings.

| Setting | Summary |
| --- | --- |
| Articulated object manipulation | 10 categories in SAPIEN, including microwave, laptop, faucet, bottle, safe, cabinet, dispenser, remote, toaster, and refrigerator tasks. |
| Rigid object manipulation | PickCube, StackCube, and PushCube, evaluated against VLA and diffusion-policy baselines. |
| Robustness analysis | Ablations on kinematic retrieval, visual grounding, anchor constraints, and dynamic replanning, plus visual corruption tests. |
| Real-world deployment | Realman RM75 robot with an Intel RealSense D435 RGB-D camera across seven manipulation categories. |

Key reported results include:

- **74% average success** on articulated-object manipulation, outperforming data-driven baselines.
- **100.0 +/- 0.00% success** on the three rigid-object manipulation tasks.
- Strong robustness under distractors, partial occlusions, and real-world sensor noise.
- Closed-loop execution at **5 Hz**, with one-time initialization separated from online control.

## Code Release

The code is not publicly released yet. This repository currently contains the paper source and project assets. We plan to release the cleaned implementation, setup instructions, and evaluation scripts after the camera-ready cleanup.

Expected release items:

- Semantic topology generation and knowledge-base querying.
- RGB-D metric visual grounding pipeline.
- Constraint-driven trajectory generation and replanning.
- Simulation and real-world evaluation scripts.

## Citation

If you find this work useful, please consider citing:

```bibtex
@inproceedings{zhang2026relafford6d,
  title     = {RelAfford6D: Relational 6D Affordance Graphs for Constraint-Driven Robotic Manipulation},
  author    = {Zhang, Guodong and He, Qichen and Xie, Wenyuan and Wu, Shaokai and Ji, Yanbiao and Li, Qiuchang and Bayramli, Bayram and Ding, Yue and Lu, Hongtao},
  booktitle = {European Conference on Computer Vision (ECCV)},
  year      = {2026}
}
```

## Contact

For questions about the paper or future code release, please open an issue or contact the authors.
