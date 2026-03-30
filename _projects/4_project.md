---
layout: page
title: OCR improvement for Robotics
description: Impact on OCR of raw image processing on low-light and blur images
img: assets/img/clahe-3level.jpg
importance: 0
category: Machine Learning
---

Often images captured in real-world settings like warehouses, shop floors, retail stores, etc. have varying lighting conditions. Many of the industrial robots are deployed in the field to collect data or automate tasks, but a crucial part of achieving this goal is to understand what the robot is looking at. One of the popular applications in warehouse automation space is multi-camera systems intended for data capture. These systems often need to read product labels and require very robust OCR text detection capabilities. OCR suffers several challenges due to the variations in font face, size, background, surface reflectivity, lighting conditions, etc. The small size of text which otherwise an OCR might infer well can become tricky if the image has blur or has low-contrast due to shadows, low-lighting, etc. In this work we employ classical image processing techniques to evaluate how OCR detection and
recognition performance is impacted on images with aforementioned artifacts. We create a dataset with a focus on realworld robotics application scenarios discussed above. Additionally we compare the improvements of image processing enhancements with OCR results obtained on a fine-tuned model.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/msrcp-3level.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/clahe-3level.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/sharpen-3level.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: MSRCP 3 level, Middle: CLAHE 3 level, Right: Edge sharpening 3 level
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/bl-deconv-3level.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Blind Deconvolution 3 level
</div>

In this project, we examined how classical image enhancement techniques affect OCR performance when images contain real-world degradations commonly seen in robotics applications. Using a diverse dataset designed to reflect practical deployment conditions, we evaluated how different enhancement methods interact with a modern end-to-end OCR model. Broadly, this study helps answer the two motivating questions
posed at the start of the project by showing when image preprocessing can be beneficial and when learning-based adaptation is more effective. Our results indicate that improving visual quality alone does not always translate to better text
recognition, and that the behavior of the OCR model must be carefully considered when designing preprocessing pipelines. More generally, this work highlights the importance of data diversity and systematic evaluation when building OCR systems
for real-world environments. By analyzing both the benefits and limitations of enhancement-based approaches, this study provides useful insights for developing more reliable OCR solutions in challenging industrial and robotic settings.
