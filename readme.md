Object Detection
====
Introduction
----
Nowadays the development of large dataset and hardware make it possible to train machine learning models over millions of examples. Video detection methods always use region-based convolutional neural networks(RCNN) to extract frame level features. And now MASK-RCCN makes it even easier to perform image segmentation with high accuracy.

R-CNN
----
R-CNN makes use of region proposal method to creat many regions of interest and they wrap the regions into a fixed size image that fitted for CNN. Then the image will be processed by CNN and we can get a 4096-dimensional feature. Many layers will classify the image. But when there are too many proposals, the R-CNN can be very slow.
Drawbacks:<br>
1.It cannot be implemented real time.<br>
2.Expensive<br>

![image](https://github.com/szyszy315/hello-world/blob/master/project2_image2.png)

Fast R-CNN
----
FastR-CNN achieves near real-time rates using very deep networks. Compared with R-CNN, Fast-RCNN is cheaper and quicker. Fast-RCNN swapes the order of getting region proposal and running the CNN, so Fast-RCNN only convert the image into the features map once. Then use Spatial Pyramid Pooling network (spp-net) to get region of interests (RoIs).RoI pooling wraps ROIs into one single layer and feeds them to fully connected layers for classification.<br>
Drawbacks:<br>
1.Selective search is a slow and time-consuming process affecting the performance of the network.<br>
2.Not flexible.
![image](https://github.com/szyszy315/hello-world/blob/master/project2_image4.png)

Faster R-CNN
----
FasterR-CNN makes use of Region Proposal Networks(RPNs) which can share convolutional layers with state-of-the-art objectdetection networks to creat region proposal. Faster-RCNN is composed of two modules. The first module is a deepfully convolutional network that proposes regions,and the second module is RPNs. RPNs takes an image as input and outputs a set of rectangular object proposals, each with  an objectness score.<br>

###Region Proposal Networks<br>
A Region Proposal Network (RPN) takes an image(of any size) as input and outputs a set of rectangularobject proposals, each  with an objectness  score.<br>

###Anchors<br>
There will be k proposals per sliding-window location, the RPNs cangenerate more proposals by changing the value of k,which is the number of maximum possible proposals for each location. The k proposals are parameterized relative to k reference boxes, which is so called anchors. An anchor is centered at the sliding windowin question, and is associated with a scale and aspect ratio. k = scale ratio * aspect ratio. The anchors are translation-invariant, if an object is translated the proposal will still be the same. Translation invariant also makes model's size smaller. <br>
![image](https://github.com/szyszy315/hello-world/blob/master/project2_image3.png)
![image](https://github.com/szyszy315/hello-world/blob/master/project2_image5.png)

Mask R-CNN
----
MaskR-CNN extends FasterR-CNN by adding a branch for predicting an object mask in parallel with the existing branch for bounding box recogni-tion.  Mask R-CNN is simple to implement andtrain given the Faster R-CNN framework, which facilitatesa wide range of flexible architecture designs. Additionally,the mask branch only adds a small computational overhead,enabling a fast system and rapid experimentation. Mask R-CNN outputs a binary mask for each RoI and the classification depends on masks, which makes this system different from others. Instance segmentation enables us to obtain a pixel-wise mask for each individual object in an image. <br>
Advantage：<br>
1.Easy to generalize to other tasks.<br>
2.Fast train and test speeds.<br>
![image](https://github.com/szyszy315/hello-world/blob/master/project2_image1.png)


Recommendations for a person who want to develop or use such systems
----
1.Users can increase the accurracy of prediction by using the result of multiple models.<br>
2.Developers should make thier methods flexible and robust so it will be much easier to improve the method.<br>

conclusion
----
The vision community has rapidly improved object detection and semantic segmentation results over a short period of time and will keep making it better in the future. A large part of these advances are the result of development of powerful  baseline  systems,  such  as  the  Fast/Faster  R-CNN and Fully Convolutional Network (FCN) frameworks for object detection. These methods are conceptually intuitiveand offer flexibility and robustness, together with fast training and inference time. <br>

references:
--- 
[1]Faster R-CNN: Towards Real-Time ObjectDetection with Region Proposal Networks, Shaoqing Ren, Kaiming He, Ross Girshick, Jian Sun<br>
[2]Mask R-CNN, Kaiming He, Georgia Gkioxari, Piotr Dollar, Ross Girshick; The IEEE International Conference on Computer Vision (ICCV), 2017, pp. 2961-2969 <br>
[3]Rethinking the Faster R-CNN Architecture for Temporal Action Localization, Yu-Wei Chao, Sudheendra Vijayanarasimhan, Bryan Seybold, David A. Ross, Jia Deng, Rahul Sukthankar; The IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2018, pp. 1130-1139<br> 

