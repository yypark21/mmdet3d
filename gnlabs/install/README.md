# Local setup

## Environment

-   OS: Ubuntu 20.04
-   GPU: NVIDIA GeForce RTX 2070 SUPER / RTX 3080
-   CUDA: 10.1.2 / 11.1.1, respectively

## Install
### conda
```bash
conda create -n gn python=3.7 -y
conda activate gn
```
### RTX 2070 case
```bash
# install PyTorch with the CUDA version
conda install pytorch==1.6.0 torchvision==0.7.0 cudatoolkit=10.1 -c pytorch
sudo apt-get update && sudo apt-get install -y ffmpeg libsm6 libxext6 git ninja-build libglib2.0-0 libsm6 libxrender-dev libxext6 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
# install mmcv
pip install mmcv-full==1.3.8 -f https://download.openmmlab.com/mmcv/dist/cu101/torch1.6.0/index.html
# install mmdetection
pip install mmdet==2.14.0
# install mmsegmentation
pip install mmsegmentation==0.14.1
```

<details>
    <summary> RTX 3080 case (shows better performance clearly but can't train MVXNet model) </summary>
    conda install pytorch==1.8.0 torchvision==0.9.0 cudatoolkit=11.1 -c pytorch -c nvidia<br/>
    pip install mmcv-full==1.4.0<br/>
    pip install mmdet==2.19.0<br/>
    pip install mmsegmentation==0.19.0
</details>

### common
```bash
# install mmdetection3d-0.17.0
git clone https://github.com/Comverser/mmdetection3d.git
cd mmdetection3d
pip install -v -e .

# compatibility error fix
pip install pycocotools==2.0.1
# install visualization package
pip install open3d
```

# set "samples_per_gpu" to 1

-   https://github.com/open-mmlab/mmdetection3d/issues/37

# Docker setup

## Environment
-   OS: Ubuntu 18.04
-   GPU: NVIDIA GeForce RTX 2070 SUPER
-   CUDA: 11.1.1 / 10.1.2

## Install
1. install docker
2. install nvidia-container-toolkit
3. build
```bash
sudo docker build -t mmdetection3d gnlabs/
```
