---
layout: page
title: Semantic mapping in indoor SLAM
description: to build a blind guiding robot
img: assets/img/seg_video_2.gif
importance: 1
category: Academic projects
related_publications: 
---

## Overview
To build a blind guiding mobile robot for an indoor environment the robot has to know its surroundings in the form of a map. The map that is generated by SLAM process will contain the depth data only. In order for the robot to locate the indoor features like doors, room numbers, elevators, water coolers, etc. there has to be semantics associated with the map. The aim of this project is to segment out the plane from depth data and place the corresponding semantic features on the correct plane in the map which are detected from object detection on the RGB image.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/seg_video_1.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/seg_video_2.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Rviz demo showing successful plane extraction of a 'door' from realtime depth data
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/map.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    figure showing the final mapping with semantic features
</div>

## Project workflow
Firstly, RANSAC segmentation was tried on one single frame of depth image. Once that was successful, code was converted to include ros subscriber and publisher for the incoming point cloud and the processed output point cloud. This was done using an artificial pcd publisher to publish the single pcd file. Command for the same is given below:

    rosrun pcl_ros pcd_to_pointcloud extracted_inliers.pcd 0.1 _frame_id:=map cloud_pcd:=orig_cloud_pcd

After this was working we moved to live data steam. On live data stream we then cropped the point cloud to hard coded bounding box frame which required extracting x,y,z data from point cloud, converting it to numpy array for slicing based on indices and the reconstructing point cloud for publishing over standard message types. After this a subscriber was created to listen to bounding box coordinates and used it to replace the hard coded bounding box indices for cropping the point cloud. After this last task of marker placement. For marker all the plane data was collected into a Float32MultiArray and published. Another node will be listening to this data and place a cuboidal marker based on this data.

## Working
1. Depth image is first received as a `PointCloud2` message by the `main_extraction()` callback function. Alongside `bounding_boxes` message is received from `darknet_ros` package by the `BBox_receiver` callback function.
2. For all the bounding boxes received, if the object Class is 'door' then the `cloud` data will be handed over to `extractor_engine_RANSAC()` to perform segmentation.
3. Coefficients of the equation of plane will be obtained from the engine. Now we will construct a `Float32MultiArray` type message to publish all the data required to place a marker. We need bounds for the size of marker.
4. The bounding box x,y data is yet in the form of image indices. To obtain the coordinates of those bounds we need to query those index values in the xyz cloud data. This is handled by `query_bounding_box_coords()` function.
5. But `xyz_array` might be having `nan` values at these index values due to absence of sensor reading there. To handle this we can recursively search for indices with 'non-nan' values. For top left corner we search one step by increasing the indices and for bottom right corner one step decreasing the indices, travelling along the diagonal. All this is done by `recursive_search_non_nan_value_decreasing()` and `recursive_search_non_nan_value_increasing()`.
6. After the plane data is published, all the extracted inliers (for each door detected) are combined into a single list and converted into and array of x,y,z points.
7. Message is constructed of type `PointCloud2` to carry the inlier data which is converted into a cloud and the message is published.
8. Inside the marker publisher node, from the plane data received orientation of marker has to be calculated in the form of quaternions. We need roll, pitch, yaw for finding quaternions. To find rpy 3 vectors are needed. One is the normal vector we directly get from a,b,c. Second we can get from any 2 bounding box coordinates. Third will be the cross product of first two vectors. Lastly marker message is published over `marker_publisher` topic.

## Sensors used
Xbox 360 Kinect sensor is used. Its range is about 5 metres which is more than Intel Realsense sensor’s range of 3 metres. The width of the image stream is 640 pixels and height is 480 pixels. An image is described like a 2D array hence, the first index which is the no. of row corresponds to the Y coordinate and second index which is the no. of columns corresponds to the X coordinate.
