# Environment

-   OS: Ubuntu 20.04
-   GPU: NVIDIA GeForce RTX 3080
-   CUDA: 11.1.1
-   Conda: Anaconda3-2021.11-Linux-x86_64

# Install

```bash
conda create -n gn python=3.7 -y
conda activate gn

# install PyTorch(1.10.1) prebuilt with the prebuilt CUDA version
conda install pytorch==1.8.0 torchvision==0.9.0 cudatoolkit=11.1 -c pytorch -c nvidia

# install mmcv
pip install mmcv-full==1.3.9

# install mmdetection
pip install mmdetection==2.19.0

# install mmsegmentation
pip install mmsegmentation==0.19.0


# install mmdetection3d-0.17.0
git clone https://github.com/Comverser/mmdetection3d-0.17.0-gnlabs.git
cd mmdetection3d-0.17.0-gnlabs
pip install -v -e .

# compatibility error fix
pip install pycocotools==2.0.1
# install visualization package
pip install open3d
```

```bash
docker build -t mmdetection3d docker/
```

# Bug

-   https://github.com/open-mmlab/mmdetection3d/issues/37

