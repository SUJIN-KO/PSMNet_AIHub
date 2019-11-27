# PSMNet_AIHub


This repository contains the inspection of NIA Sidewalk dataset provided by [AI Hub](http://www.aihub.or.kr/).
Sidewalk dataset is public data to solve that disabled person have the difficulty of walking in the sidewalk. [Download](http://www.aihub.or.kr/content/611)
This repository contains the code (in PyTorch) for "[Pyramid Stereo Matching Network](https://arxiv.org/abs/1803.08669)" paper (CVPR 2018) by [Jia-Ren Chang](https://jiarenchang.github.io/) and [Yong-Sheng Chen](https://people.cs.nctu.edu.tw/~yschen/).



본 저장소는 NIA 인도 보행 공공 데이터의 검수용으로 구축되었습니다. 인도 보행 데이터는 공공 데이터 구축을 목적으로 하는 [AI Hub](http://www.aihub.or.kr/) 에서 제공됩니다.
인도 보행 공공 데이터는 장애인 인도보행의 어려움과 이동권 문제 해결을 위하여 만들어졌습니다. [다운 링크](http://www.aihub.or.kr/content/611)
본 저장소는 "[Pyramid Stereo Matching Network](https://arxiv.org/abs/1803.08669)" 기반으로 이루어졌습니다.


## Introduction

PSMNet, a pyramid stereo matching network, consists two main modules: spatial pyramid pooling and 3D CNN.

<img align="center" src="https://user-images.githubusercontent.com/11732099/43501836-1d32897c-958a-11e8-8083-ad41ec26be17.jpg">

## Installation

### Dependencies

- [Python 2.7](https://www.python.org/downloads/)
- [PyTorch (0.4.0+)](http://pytorch.org)
- torchvision 0.2.0 (higher version may cause issues)


### Train
As an example, use the following command to train a PSMNet on Scene Flow

```
python main.py --maxdisp 192 \
               --model stackhourglass \
               --datapath (your scene flow data folder)\
               --epochs 10 \
               --loadmodel (optional)\
               --savemodel (path for saving model)
```

As another example, use the following command to finetune a PSMNet on KITTI 2015

```
python finetune.py --maxdisp 192 \
                   --model stackhourglass \
                   --datatype 2015 \
                   --datapath (KITTI 2015 training data folder) \
                   --epochs 300 \
                   --loadmodel (pretrained PSMNet) \
                   --savemodel (path for saving model)
```
You can also see those examples in run.sh.

### Evaluation
Use the following command to evaluate the trained PSMNet on KITTI 2015 test data

```
python submission.py --maxdisp 192 \
                     --model stackhourglass \
                     --KITTI 2015 \
                     --datapath (KITTI 2015 test data folder) \
                     --loadmodel (finetuned PSMNet) \
```

### Pretrained Model
- NOTE: The pretrained model were saved in .tar; however, you don't need to untar it. Use torch.load() to load it.

| KITTI 2015 |  Scene Flow | KITTI 2012| NIA Sidewalk |
|---|---|---|---|
|[Google Drive](https://drive.google.com/file/d/1pHWjmhKMG4ffCrpcsp_MTXMJXhgl3kF9/view?usp=sharing)|[Google Drive](https://drive.google.com/file/d/1xoqkQ2NXik1TML_FMUTNZJFAHrhLdKZG/view?usp=sharing)|[Google Drive](https://drive.google.com/file/d/1p4eJ2xDzvQxaqB20A_MmSP9-KORBX1pZ/view)|[Google Drive](https://drive.google.com/open?id=1S8KUz2bCRhBbj_YRyzjB03Ag_S8WJA2I)|


## Results

### Hardware

8 NVIDIA Titan Xp GPUs

Intel Xeon 4210 CPU @ 2.20GHz

### Software

Ubuntu 16.04

Python 2.7

PyTorch 0.4.0

CUDA 9.0


### Results on NIA Sidewalk dataset

| Network | Language | D1-all (All) | Download |
|--|--|--|--|
| PSMNet | Pytorch 0.4.0 | 4.779 % | [Model](https://drive.google.com/file/d/1ZWhZL_ZiwQub9ZtoNjNzLXjgLHwbF4Wm/view?usp=sharing) |


### Qualitative results
#### Left image
<img align="center" src="https://user-images.githubusercontent.com/36181879/69515135-f21e4a00-0f90-11ea-805f-8cf4fa33529f.png">

#### Predicted disparity
<img align="center" src="https://user-images.githubusercontent.com/36181879/69515137-f21e4a00-0f90-11ea-948a-af3a84dc3f5b.png">


## Contacts
parkkibaek@kaist.ac.kr

## License
MIT License

### Citation
```
@inproceedings{chang2018pyramid,
  title={Pyramid Stereo Matching Network},
  author={Chang, Jia-Ren and Chen, Yong-Sheng},
  booktitle={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition},
  pages={5410--5418},
  year={2018}
}
```