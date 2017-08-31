# Realtime Multi-Person Pose Estimation
## Introduction
Code repo for winning 2016 MSCOCO Keypoints Challenge, 2016 ECCV Best Demo Award, and 2017 CVPR Oral paper.  

Watch our video result in [YouTube](https://www.youtube.com/watch?v=pW6nZXeWlGM&t=77s) or [our website](http://posefs1.perception.cs.cmu.edu/Users/ZheCao/humanpose.mp4). 

We present a bottom-up approach for multi-person pose estimation, without using any person detector. For more details, refer to our [CVPR'17 paper](https://arxiv.org/abs/1611.08050) or our [presentation slides](http://image-net.org/challenges/talks/2016/Multi-person%20pose%20estimation-CMU.pdf) at ILSVRC and COCO workshop 2016.

This project is licensed under the terms of the [license](LICENSE).

## Results

<p align="left">
<img src="https://github.com/ZheC/Multi-Person-Pose-Estimation/blob/master/readme/dance.gif", width="720">
</p>

<p align="left">
<img src="https://github.com/ZheC/Multi-Person-Pose-Estimation/blob/master/readme/shake.gif", width="720">
</p>

## Contents
1. [Testing](#testing)
2. [Training](#training)
3. [Citation](#citation)

### Python
- `cd testing/python`
- `ipython notebook`
- Open `demo.ipynb` and execute the code

## Training

### Training Steps 
- Run `cd training; bash getData.sh` to obtain the COCO images in `dataset/COCO/images/`, keypoints annotations in `dataset/COCO/annotations/` and [COCO official toolbox](https://github.com/pdollar/coco) in `dataset/COCO/coco/`. 
- Run `getANNO.m` in matlab to convert the annotation format from json to mat in `dataset/COCO/mat/`.
- Run `genCOCOMask.m` in matlab to obatin the mask images for unlabeled person. You can use 'parfor' in matlab to speed up the code.
- Run `genJSON('COCO')` to generate a json file in `dataset/COCO/json/` folder. The json files contain raw informations needed for training.
- Run `python genLMDB.py` to generate your LMDB. (You can also download our LMDB for the COCO dataset (189GB file) by: `bash get_lmdb.sh`)
- Run `python setLayers.py --exp 1` to generate the prototxt and shell file for training.
- Run `bash train_pose.sh 0,1` (generated by setLayers.py) to start the training with two gpus. 

## Citation
Please cite the paper in your publications if it helps your research:
    
    
    @inproceedings{cao2017realtime,
      author = {Zhe Cao and Tomas Simon and Shih-En Wei and Yaser Sheikh},
      booktitle = {CVPR},
      title = {Realtime Multi-Person 2D Pose Estimation using Part Affinity Fields},
      year = {2017}
      }
	  
    @inproceedings{wei2016cpm,
      author = {Shih-En Wei and Varun Ramakrishna and Takeo Kanade and Yaser Sheikh},
      booktitle = {CVPR},
      title = {Convolutional pose machines},
      year = {2016}
      }