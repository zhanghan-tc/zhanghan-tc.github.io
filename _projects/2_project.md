---
layout: page
title: 4D Radar SLAM
description: We develop SLAM algorithm based on 4D radar data
img: assets/img/4D_radar_vehicle.png
importance: 2
category: perception
---
This project is supported by ZF (China) Investment Co., Ltd. (the legal entity of ZF Friedrichshafen AG in China).

If you are interested in the 4D radar SLAM data set, you can go [Software & Data sets](/4dradar_data) to have a look.

（See "[Xingyi Li, Han Zhang, Weidong Chen. 4D Radar-Based Pose Graph SLAM With Ego-Velocity Pre-Integration Factor, IEEE Robotics and Automation Letters, Vol. 8, Iss. 8, 5124 - 5131, August 2023](https://ieeexplore.ieee.org/document/10173499)" for more details.）

Millimeter wave (mmWave) radars have been widely exploited for Simultaneous Localization and Mapping (SLAM), especially in autonomous driving. Compared to cameras or LiDARs, mmWave radars are robust to adverse weather and light conditions, ensuring consistent reliability in diverse environments. Moreover, mmWave radars are more affordable, making them popular for integration in autonomous vehicles.

Conventional radars can be categorized into two species:
scanning radars and automotive radars [8]. In particular, scanning
radars scan the environment in 360 degrees, providing 2D
planar images without velocity information. While automotive
radars have a smaller field of view (FoV) and offer sparse
planar point clouds with relative radial Doppler velocity.
Compared to conventional radars, 4D radars have a similar
FoV to automotive radars, but provide a denser 3D point cloud with richer information, i.e., range, azimuth, elevation
and Doppler velocity. With additional
information and increased resolution, 4D radars open up new
opportunities for SLAM applications.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/4D_radar.png" title="4D radar" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-5 mt-md-0">
        {% include figure.html path="assets/img/4D_radar_doppler_vel.png" title="4D radar point cloud with doppler velocity" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    On the left, the 4D radar provided by ZF. 
    Right, 3D radar point cloud with doppler velocity.
</div>

Due to the sparsity and noisy measurements of 4D radar point clouds, SLAM methods for LiDAR would achieve a very poor performance if directly used. In addition, due to the difference in data characteristics, conventional
radar SLAM systems are no longer suitable for 4D radars. Therefore, we develop an accurate and robust SLAM framework
for 4D radars. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/4D_radar_slam_diagram.png" title="4D radar slam diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The system overview of 4DRaSLAM. Given a 4D radar point cloud with spatial information (range, azimuth, elevation) and Doppler velocity, the
spatial information is used in the 4D radar filter to reduce ghost and random points. Then we extract static points and estimate ego-velocity from the Doppler
velocity. In the pose graph optimization module, radar odometry factor (RO factor), ego-velocity pre-integration factor (EVP factor), and loop closure factor
(LC factor) are added to a pose graph. Finally, we estimate the vehicle poses and obtain a consistent global map after graph optimization.
</div>

We have tested our 4D radar SLAM algorithm in an industrial park and our campus under multiple scenarios. 
The results are shown in the video below.
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.html path="https://ieeexplore.ieee.org/ielx7/7083369/10153452/10173499/supp1-3292574.mp4?arnumber=10173499" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
