---
layout: page
title: Quadruped robot
description: build and simulate a walking four-legged robot
img: assets/img/sim-test1.gif
importance: 2
category: Academic projects
giscus_comments: false
---

## Motivation

A four-legged Quadruped robot inspired by the Boston Dynamics Spot and MIT Cheetah, a project undertaken by Team Robocon BITS Pilani. Quadruped robots have several applications like last mile delivery, as guiding robots for visually challenged idividuls, surveillance, accessing hazardous enviornments and space exploration.

The Quadruped robot community and research is growing everyday in different parts of the world. Legged robots have several advantages over wheeled counter-parts in terms of traversibility. This also makes it an excellent research platform for legged locomotion, RL, perception, controls and dynamics. With this motivation this project was taken up to simulate a walking Quadruped in Gazebo ROS.

## Simulation

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/sim-test2.gif" title="simulation trot gait" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Gazebo ROS simulation with trot gait.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/sim-test4pace.gif" title="simulation pace gait" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Gazebo ROS simulation with pace gait.
</div>

## Gait

This is how various gaits look like in a simple 2D animation.

|  |  |
| ------ | ------ |
| **Light Blue :** | Left legs |
| **Dark Blue :** | Right Legs |


<div class="row">
    <div class="col-sm mt-2 mt-md-0">
        {% include figure.html path="assets/img/trot.gif" title="trot gait animation" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-2 mt-md-0">
        {% include figure.html path="assets/img/walk.gif" title="walk gait animation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Trot gait (left), walk gait (right)
</div>

<div class="row">
    <div class="col-sm mt-2 mt-md-0">
        {% include figure.html path="assets/img/gallop.gif" title="gallop gait animation" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-2 mt-md-0">
        {% include figure.html path="assets/img/bound.gif" title="bound gait animation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Gallop gait (left), bound gait (right)
</div>

## Kinematics

The calculations for inverse kinematics have been shown in the image below

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/smai-ik1.jpg" title="inverse kinematics image 1" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Inverse Kinematics figure-1. [modified version, original image credits: a Spotmicroai community member]
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/smai-ik2.jpg" title="inverse kinematics image 2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Inverse Kinematics figure-2. [modified version, original image credits: a Spotmicroai community member]
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/smai-ik3.jpg" title="inverse kinematics image 3" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Inverse Kinematics figure-3. [modified version, original image credits: a Spotmicroai community member]
</div>

## References

* Original idea : [MIT Cheetah](https://www.youtube.com/watch?v=QZ1DaQgg3lE&ab_channel=MassachusettsInstituteofTechnology%28MIT%29) and [Spot by Boston Dynamics](https://www.bostondynamics.com/spot)
* High speed trot-running: Implementation of a hierarchical controller using proprioceptive impedance control on the [MIT Cheetah](https://dspace.mit.edu/handle/1721.1/98270)
* https://github.com/mike4192/spotMicro
* Spot mini mini : authors - Maurice Rahme and Ian Abraham and Matthew Elwin and Todd Murphey [spotminimini2020github](https://github.com/moribots/spot_mini_mini)
* Spot Micro AI Community : https://spotmicroai.readthedocs.io/en/latest/
