# Pruning

Since AlexNet won the ILSVRC 2012 ImageNet image classification competition, the convolutional neural network (CNN) boom has swept the entire computer vision field. The CNN model quickly replaced traditional hand-crafted features and classifiers, not only providing an end-to-end processing method, but also greatly refreshing the accuracy of each image competition task, and even surpassed the human eye. Accuracy (LFW face recognition task). While the CNN model is approaching the accuracy limit of computer vision tasks, its depth and size are also increasing exponentially.

Table 1 Comparison of the sizes, calculations and parameters of several classic models
<center><img src='https://github.com/kzhang14/Pruning/blob/master/resources/fig1.jpg'></center>

What follows is a very embarrassing scenario: such a huge model can only be used on a limited platform, and it cannot be transplanted to mobile terminals and embedded chips at all. Even if you want to transmit over the network, the high bandwidth consumption makes many users daunting. On the other hand, large-sized models also pose huge challenges to device power consumption and operating speed. Therefore, such a model is still far from practical.

Under such circumstances, miniaturization and acceleration of models have become urgent problems. In fact, some scholars in the early days proposed a series of compression methods for CNN models, including weight shearing (prunning) and matrix SVD decomposition, but the compression rate and efficiency are far from satisfactory.

In recent years, algorithms for model miniaturization can be roughly divided into two categories from the perspective of compression: compression from the numerical value of model weights and compression from the perspective of network architecture. On the other hand, from the perspective of taking into account the calculation speed, it can be divided into: only compressing the size and compressing the size while increasing the speed.

This article mainly discusses the following representative articles and methods, including SqueezeNet, Deep Compression, XNorNet, Distilling, MobileNet, and ShuffleNet.

Table 2 Several classic compression methods and comparison
<center><img src='https://github.com/kzhang14/Pruning/blob/master/resources/fig2.bmp'></center>

We are aiming to compress the CNN size by exploring the how much redundancy still exists in the network, by promoting certain sparse structures of the network. For the FC layer, we promote a diagonal structure which shrinks the layer size from O(NM) to O(min(M,N)). For the convolutional layer, we use the CP-decomposition and Tucker decomposition to decompose a convolution layer. Each of the above compression performing on most of the current imageset can achieve around ~1% accuracy loss, sometimes even no loss. Here we are curious to see the results of them combining together. 
