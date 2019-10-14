Object Detection
====
Introduction
----
Nowadays the development of large dataset and hardware make it possible to train machine learning models over millions of examples. Video detection methods always use region-based convolutional neural networks(RCNN) to extract frame level features. And now MASK-RCCN makes it even easier to perform image segmentation with high accuracy.

R-CNN
----
R-CNN makes use of region proposal method to creat many regions of interest and they wrap the regions into a fixed size image that fitted for CNN. Then the image will be processed by CNN and we can get a 4096-dimensional feature. Many layers will classify the image. But when there are too many proposals, the R-CNN can be very slow.
drawbacks:
1.slow
2.expensive

FastR-CNN
----
FastR-CNN achieves near real-time rates using very deep networks. Compared with R-CNN, Fast-RCNN is cheaper and quicker. Fast-RCNN swapes the order of getting region proposal and running the CNN, so Fast-RCNN only convert the image into the features map once. Then use Spatial Pyramid Pooling network (spp-net) to get region of interests (RoIs).RoI pooling wraps ROIs into one single layer and feeds them to fully connected layers for classification.
drawbacks:
1.algorithms run on CPU and they are slow.

FasterR-CNN
----
FasterR-CNN makes use of Region Proposal Networks(RPNs) which can share convolutional layers with state-of-the-art objectdetection networks to creat region proposal. Faster-RCNN is composed of two modules. The first module is a deepfully convolutional network that proposes regions,and the second module is RPNs. RPNs takes an image as input and outputs a set of rectangular object proposals, each with  an objectness score.

###Anchors

There will be k proposals per sliding-window location, the RPNs cangenerate more proposals by changing the value of k,which is the number of maximum possible proposals for each location. The k proposals are parameterized relative to k reference boxes, which is so called anchors. An anchor is centered at the sliding windowin question, and is associated with a scale and aspect ratio. k = scale ratio * aspect ratio. The anchors are translation-invariant, if an object is translated the proposal will still be the same. Translation invariant also makes model's size smaller. 

MaskR-CNN
----
MaskR-CNN extends FasterR-CNN by adding a branch for predicting an object mask inparallelwith the existing branch for bounding box recogni-tion. 
advantage：
1.easy to generalize to other tasks.
2.fast train and test speeds

Recommendations for a person who want to develop or use such systems
----
1.users can increase the accurracy of prediction by using the result of multiple models.
2.developer should concentrate more on 


references:
----
[1]Faster R-CNN: Towards Real-Time ObjectDetection with Region Proposal NetworksShaoqing Ren, Kaiming He, Ross Girshick, and Jian Sun
[2]Mask R-CNNKaiming HeGeorgia GkioxariPiotr Doll ́arRoss Girshick
