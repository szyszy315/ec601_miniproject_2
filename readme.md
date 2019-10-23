Object Detection
====
Introduction
----
Nowadays the development of large dataset and hardware make it possible to train machine learning models over millions of examples. Video detection methods always use region-based convolutional neural networks(RCNN) to extract frame level features. And now MASK-RCCN makes it even easier to perform image segmentation with high accuracy.

R-CNN
----
The Region-based CNN approach to bounding-box object detection is to attend to a manageable number of candidate object regions and evaluate convolutional networks independently on each RoI(region of interest). <br>
It consists of three modules. <br>
The first generates category-independent region proposals. These proposals define the set of candidate detection avail-able to detector. <br>
The second module is a large convolutional neural network that extracts a fixed-length feature vector from each region. <br>
The third module is a set of class- specific linear SVMs(support-vector machines ).<br>
Drawbacks:<br>
1.Training is a multi-stage pipeline. R-CNN first fine-tunes a ConvNet on object proposals using log loss. Then, it fits SVMs to ConvNet features. These SVMs act as object detectors, replacing the softmax classifier learnt by fine-tuning. In the third training stage, boundin-box regressors are learned.<br>
2.Training is expensive in space and time. For SVM and bounding-box regressor training, features are extracted from each object proposal in each image and written to disk. With very deep networks, the features require hundreds of gigabytes of storage.<br>
3.Object detection is slow. At test-time, features are extracted from each object proposal in each test image. <br>


![image](https://github.com/szyszy315/hello-world/blob/master/project2_image2.png)

Fast R-CNN
----
FastR-CNN achieves near real-time rates using very deep networks. Compared with R-CNN, Fast-RCNN is cheaper and quicker. Fast R-CNN swapes the order of getting region proposal and running the CNN, so Fast R-CNN only convert the image into the features map once. Then use Spatial Pyramid Pooling network (spp-net) to get region of interests (RoIs).RoI pooling wraps ROIs into one single layer and feeds them to fully connected layers for classification.<br>

Advantages:
1.Higher detection quality (mAP) than R-CNN, SPPnet.
2.Training is single-stage, using a multi-task loss.
3.No disk storage is required for feature caching.

Drawbacks:<br>
1.Selective search is a slow and time-consuming process affecting the performance of the network.<br>
2.Fast region-based CNNs take advantage of GPUs, while the region proposal methods used in research are implemented on the CPU, making such runtime comparisons inequitable.<br>
![image](https://github.com/szyszy315/hello-world/blob/master/project2_image4.png)

Faster R-CNN
----
FasterR-CNN makes use of Region Proposal Networks(RPNs) which can share convolutional layers with state-of-the-art objectdetection networks to creat region proposal. Faster-RCNN is composed of two modules. The first module is a deepfully convolutional network that proposes regions,and the second module is RPNs. RPNs takes an image as input and outputs a set of rectangular object proposals, each with  an objectness score.<br>

###Region Proposal Networks<br>
A Region Proposal Network (RPN) takes an image(of any size) as input and outputs a set of rectangularobject proposals, each with an objectness score.<br>

###Anchors<br>
There will be k proposals per sliding-window location, the RPNs cangenerate more proposals by changing the value of k,which is the number of maximum possible proposals for each location. The k proposals are parameterized relative to k reference boxes, which is so called anchors. An anchor is centered at the sliding windowin question, and is associated with a scale and aspect ratio. k = scale ratio * aspect ratio. The anchors are translation-invariant, if an object is translated the proposal will still be the same. Translation invariant also makes model's size smaller. <br>
![image](https://github.com/szyszy315/hello-world/blob/master/project2_image3.png)
![image](https://github.com/szyszy315/hello-world/blob/master/project2_image5.png)

Mask R-CNN
----
Mask R-CNN extends Faster R-CNN by adding a branch for predicting an object mask in parallel with the existing branch for bounding box recognition.  Mask R-CNN is simple to implement andtrain given the Faster R-CNN framework, which facilitatesa wide range of flexible architecture designs. Additionally,the mask branch only adds a small computational overhead,enabling a fast system and rapid experimentation. Mask R-CNN outputs a binary mask for each RoI and the classification depends on masks, which makes this system different from others. Instance segmentation enables us to obtain a pixel-wise mask for each individual object in an image. <br>

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
The vision community has rapidly improved object detection and semantic segmentation results over a short period of time and will keep making it better in the future. A large part of these advances are the result of development of powerful baseline  systems, such as the Fast/Faster R-CNN and Fully Convolutional Network (FCN) frameworks for object detection. These methods are conceptually intuitiveand offer flexibility and robustness, together with fast training and inference time. <br>

Group 3 Report Summary
----
    Jialun Wang
    Cagri Yoruk
    Qing Han
    Fengxu Tu
   
Jialun Wang – K-Means Clustering
----
The report concentrated on K-Means Clustering. K-Means clustering is an automatic classification method that groups observations into k clusters, in which items has nearest mean. <br>
what i learned:<br>
1.Unsupervised learning contains two main methods, clustering analysis and dimensionality reduction.<br>
2.K-means Clustering calculates the distance from each point to the center of the cluster, and select the closest point to re-center the cluster, and iterate.

Cagri Yoruk - State-of-the-art-Object-Detection-Models
----
This report focuses on Object Detection Models, including Yolo, Faster R-CNN, Mask R-CNN and Rotated Mask R-CNN.<br>
what i learned:<br>
1.YOLO is a real-time object detection system which it is fast and accurate. The network predicts 4 coordinates for each bounding box. They predict the objectness score of each bounding box with logistic regression.
2.Compared with Faster R-CNN, Mask R-CNN outputs the object mask on each Region of Interest.
3.Rotated Mask R-CNN is an implementation of Mask R-CNN relying on bounding box ambiguity to make the mask more accurate.

Qing Han - YOLO TensorFlow
----
This report focuses on YOLO which is a state-of-the-art, real-time object detection system.<br>
what i learned:<br>
1.YOLO detect straight from whole image pixels to bounding box coordinates and class probabilities and it can be completed in single pipeline, which make YOLO quicker than Faster R-CNN because R-CNN need cannot see the entire image.

Fengxu Tu - Unsupervised learning
----
This report focuses on some unsupervised learning methods such as Batch Gradient Descent Algorithm Based on Map-Reduce for Deep Unsupervised Learning.<br>
what i learned:<br>
1.unsupervised learning can increase the efficiency of learning using neural network.

references:
--- 
[1]Faster R-CNN: Towards Real-Time ObjectDetection with Region Proposal Networks, Shaoqing Ren, Kaiming He, Ross Girshick, Jian Sun<br>
[2]Mask R-CNN, Kaiming He, Georgia Gkioxari, Piotr Dollar, Ross Girshick; The IEEE International Conference on Computer Vision (ICCV), 2017, pp. 2961-2969 <br>
[3]Rethinking the Faster R-CNN Architecture for Temporal Action Localization, Yu-Wei Chao, Sudheendra Vijayanarasimhan, Bryan Seybold, David A. Ross, Jia Deng, Rahul Sukthankar; The IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2018, pp. 1130-1139<br> 

