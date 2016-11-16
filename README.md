
# tf_faster_rcnn_dynamic
-- experimental tensorflow implementation of Faster R-CNN, by (Ren, Shaoqing, et al. "Faster R-CNN: Towards real-time object detection with region proposal networks." Advances in neural information processing systems. 2015.)<br />
Layers are based on py-faster-rcnn (https://github.com/rbgirshick/py-faster-rcnn). Base trunk is a Residual Network, with options for either 50, 101, or 152 layers. Following He, Kaiming, et al. "Deep residual learning for image recognition." arXiv preprint arXiv:1512.03385 (2015)., 
the RPN is set right after conv4, followed by ROI Pooling. Layers conv5 and up serve as the "fully-connected" layers.

created by A. Labao under P. Naval of CVMIG Lab, Univ of the Philippines

# Specs
Training phase only - no testing version yet <br />
<br />
Current optimization is done using Momentum Optimizer with Nesterov Momentum. Input is an roidb pkl file similar to roidb input format for py-faster-rcnn (for PASCAL dataset).
<br />
- prepare roidb file (a sample code's [here](https://github.com/alfonsolink/roidb_maker) for creating the roidb file, but paths have to be modified to your local PASCAL VOC dataset folder - adopted from [mnc](https://github.com/daijifeng001/MNC))
- run resnet_z9_roi.py directly w/ the roidb file as input (and w/ roi_pooling_op.so installed - also better if loaded w/ pre-trained weights)

# Requirements
GTX 1070  <br />
OpenCV 3.1 <br />
Cuda 7.5+  <br />
Cudnn 5.0+  <br />
tensorflow v10+  <br />
and roi_pooling_op.so installed - check my other git repository [here](https://github.com/alfonsolink/tensorflow_user_ops) for the girshick roi_pooling tensorflow wrap.

# Notes
Results are much better if network is loaded with pre-trained imagenet weights. For this network, [this file](https://1drv.ms/f/s!AtPFjf_hfC81kUrPD2Kazg1Gtkz6) can restore imagenet weights.

Average cls training accuracy for mini-batch training set (128 rois per mini-batch) in PASCAL VOC 2012 (SDS version) is around 94%+ after 75,000 iterations

