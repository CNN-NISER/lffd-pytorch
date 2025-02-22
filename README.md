# A Light and Fast Face Detector for Edge Devices
**becauseofAI/lffd-pytorch had bugs in their code for face-detection and becauseofAI was not responding to issues. So this repo is uploaded after correcting the errors we faced when we tried testing over the WIDER-Face dataset. We trained the dataset for 2000000 intervals using CUDA 11.2 on Ubuntu 20.04. The testing phase includes code from becauseofAI/lffd-pytorch and YonghaoHe/LFFD-A-Light-and-Fast-Face-Detector-for-Edge-Devices,but we still faced errors as MXNet could not be installed in our system (MXNet is not available for CUDA 11.2 as of 11/03/21). So this repository is being uploaded in hope that someone can run it on thier system and provide this world with a working code of LFFD for face-detection :)**

## Introduction
This repo is the official PyTorch source code of paper "[LFFD: A Light and Fast Face Detector for Edge Devices](https://arxiv.org/abs/1904.10633)". Our paper presents a light and fast face detector (**LFFD**) for edge devices.
LFFD considerably balances both accuracy and latency, resulting in small model size, fast inference speed while achieving excellent accuracy.
**Understanding the essence of receptive field makes detection networks interpretable.**
  
In practical, we have deployed it in cloud and edge devices (like NVIDIA Jetson series and ARM-based embedding system). The comprehensive performance
of LFFD is robust enough to support our applications.

In fact, our method is **_a general detection framework that applicable to one class detection_**, such as face detection, pedestrian detection, 
head detection, vehicle detection and so on. In general, an object class, whose average ratio of the longer side and the shorter side is 
less than 5, is appropriate to apply our framework for detection.

Several practical advantages:
1. large scale coverage, and easy to extend to larger scales by adding more layers without much latency gain.
2. detect small objects (as small as 10 pixels) in images with extremely large resolution (8K or even larger) in only one inference.
3. easy backbone with very common operators makes it easy to deploy anywhere.

## Accuracy and Latency
on the way

## Getting Started
We re-implement the proposed method using PyTorch. The MXNet Version is [here](https://github.com/YonghaoHe/A-Light-and-Fast-Face-Detector-for-Edge-Devices)

#### Prerequirements (global)
* Python>=3.5
* numpy>=1.16 (lower versions should work as well, but not tested)
* PyTorch>=1.0.0 ([install guide](https://pytorch.org/get-started/locally/))
* cv2=3.x (pip3 install opencv-python==3.4.5.20, other version should work as well, but not tested)

> Tips: 
  * use PyTorch with cudnn.
  * build numpy from source with OpenBLAS. This will improve the training efficiency.
  * make sure cv2 links to libjpeg-turbo, not libjpeg. This will improve the jpeg decode efficiency.

#### Sub-directory description
* [face_detection](face_detection) contains the code of training, evaluation and inference for LFFD,
the main content of this repo. The trained models of different versions are provided for off-the-shelf deployment.
* [head_detection](head_detection) contains the trained models for head detection. The models are obtained by the
proposed general one class detection framework.
* [pedestrian_detection](pedestrian_detection) contains the trained models for pedestrian detection. The models are obtained by the
proposed general one class detection framework.
* [vehicle_detection](vehicle_detection) contains the trained models for vehicle detection. The models are obtained by the
proposed general one class detection framework.
* [ChasingTrainFramework_GeneralOneClassDetection](ChasingTrainFramework_GeneralOneClassDetection) is a simple 
wrapper based on MXNet Module API for general one class detection.

#### Installation
1. Download the repo:
```
git clone https://github.com/CNN-NISER/lffd-pytorch.git
```
2. Refer to the corresponding sub-project for detailed usage. Now only the v2 version of [face_detection](face_detection) can be tried to train.

## Citation
If you benefit from our work in your research and product, please kindly cite the paper
```
@inproceedings{LFFD,
title={LFFD: A Light and Fast Face Detector for Edge Devices},
author={He, Yonghao and Xu, Dezhong and Wu, Lifang and Jian, Meng and Xiang, Shiming and Pan, Chunhong},
booktitle={arXiv:1904.10633},
year={2019}
}
```
