<div align="center">
<h1>DA-NBV: A Direction-Aware Next-Best-View Planner for Efficient 3D  Reconstruction of Ships at Sea</h1>

<div>
  Jiaming Chen;
  Juntao Yang;
  Zhentao Zou;
  Qi Ming;
  Zhihang Zhong;
  <a href='https://yangxue.site/' target='_blank'>Xue Yang</a><sup></sup>&emsp;
  <a href='https://ee.sjtu.edu.cn/FacultyDetail.aspx?id=53&infoid=66' target='_blank'>Xue Jiang</a><sup></sup>&emsp;
  <a href='https://zytx121.github.io/' target='_blank'>Yue Zhou</a><sup></sup>&emsp;
</div>

<div>
    <sup></sup>East China Normal University&emsp; 
    <sup></sup>Shanghai Jiao Tong University &emsp; 
</div>

</div>

<p align="center">
    <img src="https://i.imgur.com/waxVImv.png" alt="Oryx Video-ChatGPT">
</p>

---

## Abstract

<div align="center">
  <img src="Figures/compare.png" width=100%>
  <div style="display: inline-block; color: #999; padding: 2px;">
      Comparison of conventional and DA-NBV scanning strategies.
  </div>
</div>

Accurate 3D reconstruction of ships at sea is important for maritime supervision, damage assessment, and autonomous maritime operations. Although 3D reconstruction has advanced considerably, high-quality data acquisition still largely relies on manually designed trajectories or skilled operators, resulting in high costs and limited scalability. Next-best-view (NBV) planning automates this process by selecting subsequent viewpoints based on the current state.
However, existing NBV policies mainly model spatial occupancy while overlooking directional observation history. This limitation is particularly problematic for ships: their complex superstructures and severe self-occlusions require observations from multiple viewpoints, and insufficient directional coverage often yields incomplete reconstructions. These challenges are further amplified at sea, where wave-induced heave, roll, and pitch continuously alter the ship's pose and surface visibility. Meanwhile, wind disturbances and limited onboard power impose stricter requirements on scanning efficiency.
To address these challenges, we propose DA-NBV, a direction-aware NBV policy that augments the conventional occupancy state with directional observation statistics. We introduce a learnable Position Advantage Field (PAF) that uses directional information to guide viewpoint selection. The policy further adopts a locally constrained action space and a nonlinear coverage-shaping reward to improve scanning efficiency. We also develop the ship-oriented SeaShip-3D dataset and a configurable sea-state simulation environment. Experiments under varying heave, roll, and pitch conditions show that DA-NBV improves reconstruction completeness by approximately 3 percentage points and reduces Chamfer distance by 43\% while achieving higher path efficiency.

---

## Maritime Simulation Environment
<div align="center">
  <img src="Figures/environment.gif" width=100%>
  <div style="display: inline-block; color: #999; padding: 2px;">
  </div>
</div>
We develop a simulation environment for offshore scanning tasks that models realistic wind and wave disturbances.

---

## SeaShip-3D Dataset
<div align="center">
  <img src="Figures/SeaShip-3D dataset.gif" width=100%>
  <div style="display: inline-block; color: #999; padding: 2px;">
  </div>
</div>

We construct the SeaShip-3D dataset, which contains 300 ship models with diverse geometric structures and detailed textures.

---

## Model and Benchmark
<div align="center">
  <img src="Figures/da_nbv_framework.png" width=100%>
  <div style="display: inline-block; color: #999; padding: 2px;">
  </div>
</div>

Overview of DA-NBV.
Motion-compensated depth observations update the occupancy grid, voxel-wise direction-vector grid, and geometric complexity grid .
The Learnable Position Advantage Scorer (LPAS) evaluates voxel--candidate-position pairs using viewing-direction alignment, visibility, distance, and geometric complexity, and aggregates their utilities into the PAF.
The encoded occupancy, PAF, UAV state, and action history are fused to predict position, orientation, and termination.

---

<div align="center">
  <img src="Figures/table.png" width=100%>
  <div style="display: inline-block; color: #999; padding: 2px;">
  </div>
</div>

DA-NBV outperforms the baselines in reconstruction completeness, accuracy, and acquisition efficiency across the evaluated dynamic sea environment and both static datasets. Compared with existing methods, DA-NBV achieves greater surface coverage with higher path efficiency. Moreover, DA-NBV remains competitive on Houses3K and OmniObject3D, indicating its generalizability to different types of static objects.

---

<div align="center">
  <img src="Figures/reconstruction.png" width=100%>
  <div style="display: inline-block; color: #999; padding: 2px;">
  </div>
</div>

DA-NBV produces more complete reconstructions with finer geometric details.

---


