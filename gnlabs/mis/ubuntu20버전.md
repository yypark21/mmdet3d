
터미널 열기

*단축키 Ctrl + Alt + T : 터미널 실행*

```bash
$ sudo apt-get update -y && sudo apt-get upgrade -y #업데이트 및 업그레이드

$ hostnamectl #우분투 버전확인 명령어
# Ubuntu 20.04.3 lts

$ python3 --version #파이썬 버전 확인

#python3 3.8.10 (이미 설치 되어 있음)

```


#
## Anaconda 설치 (2019 버전)
#
```bash
$ cd tmp/ #tmp 로 위치 변경하여 설치

$ wget https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh

$ source ~/.bashrc #설치 활성화
```

- *conda 종료 명령어*
```bash
$ conda deactivate
```
#
## cuda 11.1설치
#
```bash
$ wget https://developer.download.nvidia.com/compute/cuda/11.1.0/local_installers/cuda_11.1.0_455.23.05_linux.run

$ sudo sh cuda_11.1.0_455.23.05_linux.run
```
#
## 오류 발생시( gcc 미설치시 발생할 수 있음)
```bash
$ sudo apt install gcc 
#이전 버전과 다르게 파이썬을 설치하지 않아 gcc가 존재 하지 않아 발생한 오류 gcc version 9.3.0
```
#

## 경로설정 
#

```bash
$ sudo sh cuda_11.0.2_450.51.05_linux.run

$ vi ~/.bashrc #경로 설정하는 파일 열기 

# i를 사용해서 입력 가능 
# Esc 키 사용하여 파일 나간 후 Shift + : 을 누른 후 exit로 파일 종료 가능 

export PATH=/usr/local/cuda-11.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-11.0/lib64:$LD_LIBRARY_PATH
#경로 추가

source ~/.bashrc #변경된 부분 적용

$ nvcc --version #확인 (버전 확인이 안될시 reboot)
```

- Driver을 제외하고 설치 (이 컴퓨터의 gpu에 맞는 470 Driver을 따로 설치하기 위함)
 
   product: GP104 [GeForce GTX 1070]
#
## nvidia driver 설치
#
```bash
$ sudo apt install nvidia-driver-470 # 설치

$ sudo reboot # 재부팅

$ nvidia-smi # 확인
```

#
## pytorch 설치 (1.9.0)
#

```bash
$ conda install pytorch torchvision torchaudio cudatoolkit=11.1 -c pytorch -c nvidia

#설치 확인
$ python

import torch

print(torch.__version__) 
```

#
## mmcv 설치
#
```bash
$ pip install mmcv-full -f https://download.openmmlab.com/mmcv/dist/cu111/torch1.9.0/index.html 
#최신버전 mmcv 설치 방법
```
#


sudo apt-get install git


```bash
$ conda create -n open-mmlab python=3.7 -y
$ conda activate open-mmlab

#설치를 했어도 처음부터 다 실행해야지 오류가 발생하지 않음

# install latest PyTorch prebuilt with the default prebuilt CUDA version (usually the latest)
$ conda install -c pytorch pytorch torchvision -y

# install mmcv
$ pip install mmcv-full

# install mmdetection
$ pip install git+https://github.com/open-mmlab/mmdetection.git

# install mmsegmentation
$ pip install git+https://github.com/open-mmlab/mmsegmentation.git

# install mmdetection3d
$ git clone https://github.com/open-mmlab/mmdetection3d.git
cd mmdetection3d
pip install -v -e .

# mmdet-2.16.0
```


```bash
pip uninstall numpy
pip install numpy
# mmdet3d<1.20.0 으로 설치하라고 뜨지만 최신 버전으로 설치 해야 돌아감.
# ubuntu 18.4 버전에서는 1.19.0 버전에서 돌아갔지만 ubuntu 20에서는 안되서 최신 버전으로 설치

pip install open3d # show 명령어 실행을 위해 설치
```

```bash
# checkpoints 폴더 생성 후 모델 다운로드 
$ mkdir checkpoints

$ wget https://download.openmmlab.com/mmdetection3d/v0.1.0_models/second/hv_second_secfpn_6x8_80e_kitti-3d-car/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth
```

```bash
python demo/pcd_demo.py demo/data/kitti/kitti_000008.bin configs/second/hv_second_secfpn_6x8_80e_kitti-3d-car.py checkpoints/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth --show

```