# Environment

-   OS: Ubuntu 20.04
-   GPU: NVIDIA RTX 3080
-   CUDA: 11.3
-   Conda: Anaconda3-2021.11-Linux-x86_64

# Install

```bash
conda create -n gn python=3.7 -y
conda activate gn

# install latest PyTorch prebuilt with the default prebuilt CUDA version (usually the latest)
conda install -c pytorch pytorch torchvision -y
# conda install pytorch torchvision cudatoolkit=11.3 -c pytorch -c nvidia

# install mmcv-1.4.0
pip install mmcv-full

# install mmdetection-2.19.0
pip install git+https://github.com/open-mmlab/mmdetection.git

# install mmsegmentation-0.19.0
pip install git+https://github.com/open-mmlab/mmsegmentation.git


# install mmdetection3d-0.17.0
git clone https://github.com/Comverser/mmdetection3d-0.17.0-gnlabs.git
cd gnlabs_mmdetection3d
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

# etc

## Anaconda 설치 (2019 버전)

```bash
cd tmp/ #tmp 로 위치 변경하여 설치

wget https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh

source ~/.bashrc #설치 활성화
```
