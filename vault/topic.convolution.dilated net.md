---
id: a530b492-b21f-459b-9a24-6de26384856d
title: Dilated net
desc: ''
updated: 1601115011927
created: 1601115011927
stub: false
---
# Dilated net

- Removes the stride of convolutional layers and adds holes between each location of convolution filters. To ease the side effect of down-sampling while maintaining the expansion rate for receptive fields. It is a de facto paradigm for semantic segmentation. #definition

    #### Issues:
    1. Prior works show that lower layers tend to capture local features such as corners or edge/color conjunctions, while higher layers tend to capture more complex patterns such as parts of some objects. So using the features with the high-level semantics is unfit to segment perceptual attributes at multiple levels, especially the low-level ones.
    2. With deep layers like [[ResNet 101]], in a dilated segmentation framework, dilated convolution needs to be applied to both blocks to ensure that the max down-sampling rate of all feature maps does not exceed 8. But due to the feature maps within the two blocks are ^^increased to 4 or 16 times^^ of their designated sizes, both the computation complexity and GPU memory footprint are dramatically increased.
