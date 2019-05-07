---
title:  "Unsupervised Image Segmentation"
subtitle: ""
author: "praps"
avatar: "img/authors/wferr.png"
image: "img/seg.png"
date:   2019-05-06 12:12:12
---


### Image Segmentation
According to Wikipedia, Image segmentation is the process of partitioning a digital image into multiple segments (sets of pixels, also known as super-pixels). Each of those segments can be understood as a collection of similar pixels based on properties like brightness, pixel values etc. Image segmentation can be used in many applications like object detection, medical imaging, object recognition and so on.


### Methods for Unsupervised Image SEgmentation
We will be discussing about two deep learning approaches to solve the problem of unsupervised Image segmentation.


### Method 1: Unsupervised Image Segmentation by BackProapagation
Given an RGB image where each pixel is a 3-dimensional vector([r,g,b]), this method computes a feature vector for each pixel by passing it through a convolutional network and then the pixels are assigned labels using the method of k-mean clustering.

Let $x_n$ be the feature vector for the $n_{th}$ pixel in the image and $f(x_n)$ be a function which predicts the cluster label $c_n$ for the particular pixel. Now we have three things,$x_n$, $f(x_n)$ and $c_n$ which need to be trained. We do this by alternately fixing parameters for two things and training the third function. For example, if $c_n$ is being predicted we keep $x_n$ and $f(x_n)$ constant. The weights are updated by using backpropagation method using stochastic gradient optimizer.

For good segmentation, certain characteristics are required for the cluster label $c_n$. Instance of any object contains patches of similar texture patterns. This is taken into account while performing the segmentation. Hence, spatially continuous pixels that have similar color and texture patterns should be grouped together. On the other hand, different object instances should be categorized separately. To facilitate this cluster separation, the number of cluster labels is desired to be large. CNN architecture is used to extract the pixel features. This CNN assigns the cluster labels to image pixels and updates the convolutional filters for better separation of clusters. Backpropagation of softmax loss is used to update the network. The model architecture is given below:

![png](1.png)


