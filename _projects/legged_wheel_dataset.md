---
layout: page
title: Legged-wheel robot SLAM dataset
permalink: /legged_wheel_dataset/
---


# Introduction
We present 5  datasets of legged-wheel robot containing LiDAR data, IMU data, joint sensors data and ground truth. These datasets cover different challenging scenes. To the best of our knowledge, there are limited public datasets collected from legged-wheel robots. We hope our datasets enable the development of legged-wheel robot SLAM in the community.

Our datasets are now available at [here](https://drive.google.com/drive/folders/1NHJqMZAv29YUYVwqYfAKrgpfNtW15J1Y?usp=sharing).

# Sensor setup
The legged-wheel robot we used to collect datasets is shown in Fig. 1. It's equipped with 2 MID360 LiDAR, a BG-610M RTK GNSS, and a Realsense d435i RGB-D camera. Note that our datasets only include the LiDAR and IMU data from 2 MID360 LiDAR, the GPS-RTK data from RTK GNSS module and joints sensors data from the robot's API. Data from d435i is not in the datasets.
<div class="row">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/legged_wheel_robot.png" title="the legged-wheel robot" class="img-fluid rounded z-depth-1 w-50" %}
    </div>
</div>
<div class="caption">
    Fig. 1. Our data collection platform.
</div>

- LiDAR1(top-mounted, upside-down)：This LiDAR is mounted upside-down on the top of the robot. Its z-axis points downward, x-axis points forward along the robot’s heading direction, and the y-axis is determined by the right-hand rule (pointing to the robot’s left). It outputs 10 Hz LiDAR point cloud( topic: /livox/lidar_10_192_1_141) and 200 Hz IMU data( topic: /livox/imu_10_192_1_141).

- LiDAR2(front-mounted): This LiDAR is mounted on the front of the robot. Its pose relative to LiDAR1 is given by the extrinsic transformation as shown in Fig. 2. It outputs 10 Hz LiDAR point cloud( topic: /livox/lidar_10_192_1_123) and 200 Hz IMU data( topic: /livox/imu_10_192_1_123).
<div class="row">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/extri_l2_wrt_l1.png" title="the extrinsics" class="img-fluid rounded z-depth-1 w-50" %}
    </div>
</div>
<div class="caption">
    Fig. 2. The extrinsic of LiDAR2 w.r.t. LiDAR1.
</div>

- The GNSS system has a centimeter-level localization ability and provides the vehicle's ground truth pose in the Universal Transverse Mercator (UTM) coordinate system, at a frequency of 10 Hz.

- The joint sensors output the joint position at a high frequency of 500 Hz( topic: /joint_states). 
    - For a detailed robot description, please refer to [here](https://github.com/limxdynamics/). 
    - For a detailed data structure of joint position, please refer to [here](https://cwjgfm21di.feishu.cn/wiki/Rj6mwC4ewiDup7kzZKFcT8fGnIb)

# Data Collection
We collect the dataset in different challenging scenes in the campus of Shanghai Jiao Tong University. During the data collection process, the average robot speed is under 1m/s. In particular:
- Staircase Scene 1 & 2: different staircases with step heights 5–15 cm, 1–8 steps, feature-rich railings on one side vs. feature-scarce on the other, including single-pass and multiple back-and-forth traversals.
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/staircase1.jpg" title="the staircase1" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/staircase2.jpg" title="the staircase2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fig. 3. Left: staircase Scene 1 Dataset; Right: Staircase Scene 2 Dataset
</div>

- Artificial Hill: stone-slab path with multiple single-step ledges; walked from the base to the summit and descend via the back trail, exhibiting pronounced elevation changes and varied surface textures.
<div class="row">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/artificial_hill.jpg" title="the artifitial hill" class="img-fluid rounded z-depth-1 w-50" %}
    </div>
</div>
<div class="caption">
    Fig. 4. Artificial Hill Dataset
</div>

- Rose Garden: paths interleaving short staircase and gently undulating grass fields, with low obstacles (flower beds, shrubs) providing moderate feature density. In addition, the staircase is flanked by walls, which leads to sparse features.
<div class="row">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/rose_garden.jpg" title="the rose garden" class="img-fluid rounded z-depth-1 w-50" %}
    </div>
</div>
<div class="caption">
    Fig. 5. Rose Garden Dataset
</div>

- Botanical Garden: a route that covers a suspension bridge, an arch bridge, and flat paved sections; the dynamic sway on the suspension bridge and curved elevation on the arch pose challenges for SLAM.
<div class="row">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/botanical.jpg" title="the botanical garden" class="img-fluid rounded z-depth-1 w-50" %}
    </div>
</div>
<div class="caption">
    Fig. 6. Botanical Garden Dataset
</div>

# License
This dataset is licensed under the Creative Commons Attribution 4.0 International License (CC BY 4.0).