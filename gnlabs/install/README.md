# Local setup

## Environment

-   OS: Ubuntu 20.04
-   GPU: NVIDIA GeForce RTX 3080
-   CUDA: 11.1.1

## Install

```bash
conda create -n gn python=3.7 -y
conda activate gn

# install PyTorch with the CUDA version
conda install pytorch==1.8.0 torchvision==0.9.0 cudatoolkit=11.1 -c pytorch -c nvidia
# pip install mmcv-full

# install mmcv
pip install mmcv-full==1.4.0

# install mmdetection
pip install mmdet==2.19.0

# install mmsegmentation
pip install mmsegmentation==0.19.0

# install mmdetection3d-0.17.0
git clone https://github.com/Comverser/mmdetection3d.git
cd mmdetection3d
pip install -v -e .

# compatibility error fix
pip install pycocotools==2.0.1
# install visualization package
pip install open3d
```

# Bug

-   https://github.com/open-mmlab/mmdetection3d/issues/37

# Docker setup

## Environment
-   OS: Ubuntu 18.04
-   GPU: NVIDIA GeForce RTX 2070 SUPER
-   CUDA: 11.1.1

## Install
1. install docker
2. install nvidia-container-toolkit
3. build
```bash
sudo docker build -t mmdetection3d docker/
```
