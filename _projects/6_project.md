---
layout: page
title: LiDAR SLAM
description: LiDAR inertial SLAM from scratch
img: assets/img/data20_occ_sm_all_traj.png
importance: 0
category: Perception, Localization, Robotics
---

# LiDAR inertial 2D SLAM and RGB-D Texture Mapping
**Technologies:** Python, NumPy, SciPy, GTSAM, OpenCV

In this project I develop a complete Simultaneous Localization and Mapping (SLAM) pipeline from scratch using wheel encoder + IMU based trajectory as an initial guess for 2D LiDAR pointcloud scan matching using ICP solver. Finally texture mapping is done using RGB pixels projected to the ground plane using the robot poses.

There are following main components in this project:

* **Scan Matching & Odometry:** Implemented the Iterative Closest Point (ICP) algorithm with a Kabsch solver to align 2D LiDAR point clouds, using time-synchronized wheel odometry for robust initial pose estimation.
* **Probabilistic Mapping:** Built a log-odds Occupancy Grid Mapping system using Bresenham's ray tracing algorithm to efficiently model free space and obstacles while avoiding numerical underflow.
* **Pose Graph Optimization (PGO):** Mitigated cumulative drift by architecting a factor graph in GTSAM. Implemented custom spatial-proximity and fixed-interval loop closure detection with Mean Squared Error (MSE) consistency checks to snap the global trajectory into place.
* **Sensor Fusion & 3D Projection:** Synchronized irregular, multi-rate RGB-D (Kinect) sensor data. Performed inverse pinhole projection and rigid body transformations to project colored pixels from the optical frame to the optimized world frame, thresholding for the ground plane to generate a seamless 2D floor texture map.

# Results

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/data20_occ_odom_all_traj.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/data20_occ_sm_all_traj.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/data20_occ_opti_all_traj.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Occupancy grid map for dataset 20 using wheel odom (left), scan matching (middle), optimized (right) trajectory
</div>


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/data21_occ_odom_all_traj.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/data21_occ_sm_all_traj.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/data21_occ_opti_all_traj.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Occupancy grid map for dataset 21 using wheel odom (left), scan matching (middle), optimized (right) trajectory
</div>


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/drill.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    ICP pointcloud matching results for drill object.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/liq_container.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    ICP pointcloud matching results for liquid container object.
</div>

