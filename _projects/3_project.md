---
layout: page
title: Smart Traffic Monitoring System
description: smart control of traffic lights based on traffic detection using CV
img: assets/img/iot-desc.jpg
importance: 3
category: Academic projects
---

## Project Description

Integrating computer vision-based object detection and segmentation to gauge vehicle density on a road crossing for smart traffic light control with priority actuation based on classification of the traffic and simultaneous live data update on cloud for further analysis and visualization.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/iot-desc.jpg" title="iot description" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Project description image as a collage of different project snapshots
</div>

## Build Flow

1. Assigned labels to images for training.
2. Building Tensorflow from source
3. Training the custom object detection model on Tensorflow to detect green ball as ordinary
vehicle and red ball as emergency vehicle.
4. Converting the frozen label-map to .tflite model for running on RPi
5. Creating Frontend for data display using Flask. Bokeh with google maps API used for traffic
statistics visualization.
6. Integrating LED actuation with object detection script and testing it on a physical model made
using balls and cardboard streets.
7. Saving the detected objects in a csv file using pandas
8. Uploading the data to google spreadsheets using webhooks API
9. Hosting the Flask webpage on Azure VM


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/iot-arch.jpg" title="iot architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    IOT project architecture
</div>


## Smart traffic management system architecture and working

- Camera feeds data to RPi via one of its physical ports
- RPi uses pre-trained TFlite model and its corresponding framework to detect the objects and create .CSV file
- RPi controls the traffic light based on the traffic density. High traffic lanes are prioritized if the opposite lane is empty.
- In case of an emergency vehicle, the corresponding lane is given higher priority.
- RPi authenticates Azure VM for sending the CSV file and Video stream.
- Azure VM stores the incoming data to its system.
- Azure VM hosts flask based web page which displays the latest traffic information in a table
- Google maps API is used to visualize the traffic statistics.
- User requests the web page using the URL.
- Web page is displayed over a secure protocol.


## Practical use case

Often due to rigid traffic light switching time at an intersection a busy lane might have to get clogged with traffic while the other lane is free. With smart detection of density on any lane, light duration can be varied dynamically according to the traffic behaviour. This design also enables the prioritisation of a particular lane if any emergency vehicle is approaching so as to avoid jams in that particular lane.