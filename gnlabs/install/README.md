# Bug
- https://github.com/open-mmlab/mmdetection3d/issues/37

# Environment
- OS: Ubuntu 20.04
- GPU: NVIDIA RTX 3080
- CUDA: 11.3
- Conda: Anaconda3-2021.11-Linux-x86_64

```bash
conda create -n gn python=3.7 -y
conda activate gn

# install latest PyTorch prebuilt with the default prebuilt CUDA version (usually the latest)
conda install -c pytorch pytorch torchvision -y

# install mmcv (1.4.0)
pip install mmcv-full

# install mmdetection (2.19.0)
pip install git+https://github.com/open-mmlab/mmdetection.git

# install mmsegmentation (0.19.0)
pip install git+https://github.com/open-mmlab/mmsegmentation.git

# install mmdetection3d (mmdet3d 0.17.2)
git clone https://github.com/Comverser/gnlabs_mmdetection3d.git
cd gnlabs_mmdetection3d
pip install -v -e .
pip install pycocotools==2.0.1
pip install open3d
```
```bash
docker build -t mmdetection3d docker/
```






```bash
conda install pytorch==1.9.0 cudatoolkit=11.1 torchvision==0.9.0 -c pytorch
pip install mmcv-full==1.3.9 -f https://download.openmmlab.com/mmcv/dist/cu111/torch1.9.0/index.html 
```

# Install (updated on 2021 Dec.)
```bash
sudo apt-get update -y && sudo apt-get upgrade -y
```

## Anaconda 설치 (2019 버전)
```bash
cd tmp/ #tmp 로 위치 변경하여 설치

wget https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh

source ~/.bashrc #설치 활성화
```

- *conda 종료 명령어*
```bash
conda deactivate
```

## cuda 11.1설치
```bash
wget https://developer.download.nvidia.com/compute/cuda/11.1.0/local_installers/cuda_11.1.0_455.23.05_linux.run

sudo sh cuda_11.1.0_455.23.05_linux.run
```
### 오류 발생시( gcc 미설치시 발생할 수 있음)
```bash
$ sudo apt install gcc 
#이전 버전과 다르게 파이썬을 설치하지 않아 gcc가 존재 하지 않아 발생한 오류 gcc version 9.3.0
```

### 경로설정 

```bash
vi ~/.bashrc #경로 설정하는 파일 열기 
```

```
#경로 추가
export PATH=/usr/local/cuda-11.1/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-11.1/lib64:$LD_LIBRARY_PATH
```

```bash
source ~/.bashrc #변경된 부분 적용

nvcc --version #확인 (버전 확인이 안될시 reboot)
```

- Driver을 제외하고 설치 (이 컴퓨터의 gpu에 맞는 470 Driver을 따로 설치하기 위함)

## nvidia driver 설치
```bash
sudo apt install nvidia-driver-470 # 설치

sudo reboot # 재부팅

nvidia-smi # 확인
```


## pytorch 설치 (1.9.0)
```bash
conda install pytorch torchvision torchaudio cudatoolkit=11.1 -c pytorch -c nvidia
```

```bash
#설치 확인
python

import torch

print(torch.__version__) 
```


## mmcv 설치
```bash
pip install mmcv-full -f https://download.openmmlab.com/mmcv/dist/cu111/torch1.9.0/index.html 
#최신버전 mmcv 설치 방법
```

## Again 
```bash
conda create -n open-mmlab python=3.7 -y
conda activate open-mmlab

#설치를 했어도 처음부터 다 실행해야지 오류가 발생하지 않음
pip install numpy==1.19.0
pip install pycocotools==2.0.1
pip install open3d==0.10.0

# install latest PyTorch prebuilt with the default prebuilt CUDA version (usually the latest)
conda install -c pytorch pytorch torchvision -y

# install mmcv
pip install mmcv-full==1.3.13

# install mmdetection
pip install mmdet==2.14.0

# install mmsegmentation
pip install mmsegmentation==0.14.1

# install mmdetection3d
git clone https://github.com/Comverser/gnlabs_mmdetection3d.git
cd <project folder>

pip install -v -e .  # or "python setup.py develop"

# MMDetection3D V0.17.2 Release

# mmdet-2.16.0
```

<!-- ### Error case
```bash
pip uninstall numpy
pip install numpy
# mmdet3d<1.20.0 으로 설치하라고 뜨지만 최신 버전으로 설치 해야 돌아감.
# ubuntu 18.4 버전에서는 1.19.0 버전에서 돌아갔지만 ubuntu 20에서는 안되서 최신 버전으로 설치

pip install open3d # show 명령어 실행을 위해 설치
``` -->
