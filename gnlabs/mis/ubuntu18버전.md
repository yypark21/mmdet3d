
#
https://mmdetection3d.readthedocs.io/en/latest/
#
# Prerequisites

Linux or macOS (Windows is not currently officially supported)

Python 3.6+

PyTorch 1.3+

CUDA 9.2+ (If you build PyTorch from source, CUDA 9.0 is also compatible)

GCC 5+

MMCV
#


## Install
```bash
$ sudo apt update && sudo apt upgrade -y
```
#


## **파이썬3 설치 과정**

#
```bash
$ sudo apt install software-properties-common
```

```bash
$ sudo add-apt-repository ppa:deadsnakes/ppa
```

```bash
$ sudo apt install python3.7
```

```bash
$ sudo apt install -y python3-pip
```

Install Additional Tools

```bash
$ sudo apt install build-essential libssl-dev libffi-dev python3-dev
```

```bash
$ sudo apt install -y python3-venv
```
```bash
$ alias python='python3'

$ python3.7 -V 

#Python 3.7.11
```


#
## **2019년 버전 anaconda (4.7.12) 설치 (pytorch 에서 권장, mmdetection 3d 설치시 필요)**
#

```bash
$ sudo apt-get update -y && sudo apt-get upgrade -y
```

tmp 로 위치 변경하여 설치 
 
```bash
$ cd tmp/

$ wget https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh
```

제대로 설치 됬는지 확인하는 명령어

```bash
$ md5sum Anaconda3-2019.10-Linux-x86_64.sh

#b77a71c3712b45c8f33c7b2ecade366c  Anaconda3-2019.10-Linux-x86_64.sh

```


파일 실행 
```bash
$ bash Anaconda3-2019.10-Linux-x86_64.sh
```

설치 활성화

```bash
$ source ~/.bashrc
```

※ 오류 발생시 경로 설정 필요

- conda 종료 명령어
```bash
$ conda deactivate
```
#

## **cuda 설치**
#
https://mmcv.readthedocs.io/en/latest/get_started/installation.html


우분투 버전확인 명령어 
```bash
$ hostnamectl 

# Ubuntu 18.04.5 LTS
```


#
cudatoolkit 9.2 documentation
https://docs.nvidia.com/cuda/archive/9.2/cuda-installation-guide-linux/index.html

- Ubuntu 17.10, Ubuntu 16.04.4
#
cudatoolkit 10.1 documentation
https://docs.nvidia.com/cuda/archive/10.1/cuda-installation-guide-linux/index.html

- Ubuntu 18.10, Ubuntu 18.04.3, Ubuntu 16.04.6, Ubuntu 14.04.6 
#
cudatoolkit 10.2 documentation
https://docs.nvidia.com/cuda/archive/10.2/cuda-installation-guide-linux/index.html

- Ubuntu 18.04.3, Ubuntu 16.04.3
#

  *cuda 9.2, 10.1, 10.2 는 Ubuntu 18.04.5를 지원하지 않아서 cuda 11.0 버전을 설치* 

#
cudatoolkit 11.0 documentation https://docs.nvidia.com/cuda/archive/11.0/cuda-installation-guide-linux/index.html

- Ubuntu 20.04, Ubuntu 18.04.z (z <= 4), Ubuntu 16.04.z (z <= 6)

#
cudatoolkit 11.1 documentation
https://docs.nvidia.com/cuda/archive/11.1.0/cuda-installation-guide-linux/index.html

Ubuntu 16.04.z (z <= 7), Ubuntu 18.04.z (z <= 5), Ubuntu 20.04.1

https://developer.nvidia.com/cuda-11.0-download-archive?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=runfilelocal 


#
## 11.0 삭제 후 11.1버전으로 재설치
#
- runfile(local) 선택

```bash
$ wget http://developer.download.nvidia.com/compute/cuda/11.0.2/local_installers/cuda_11.0.2_450.51.05_linux.run

$ sudo sh cuda_11.0.2_450.51.05_linux.run

# ssh로 실행시 화면 깨짐 현상이 발생할 수 도 있음.
# 시간이 다소 걸림
```


-> Installation failed, See log at /var/log/cuda-installer.log for details 


#

## **nvidia driver 설치** 

(https://www.cyberciti.biz/faq/ubuntu-linux-install-nvidia-driver-latest-proprietary-driver/ 참조)

GPU 정보확인 명령어

```bash
$ sudo lshw -C display

# product: GP104 [GeForce GTX 1070] 
```

Ubuntu Install Nvidia driver using the CLI method

```bash
$ sudo apt-get update
```

설치 가능한 nvidia-driver 확인 명령어
```bash
$ apt search nvidia-driver
```


```bash
$ sudo apt install ubuntu-drivers-common  #ubuntu-drivers 명령어 관련 패키지

$ ubuntu-drivers devices # 내 컴퓨터에 맞는 드라이버를 추천 해주는 명령어 

#driver   : nvidia-driver-470 - distro non-free recommended

$ sudo apt install nvidia-driver-470 # 설치

$ sudo reboot # 재부팅

$ nvidia-smi # 확인
```

```bash
$ sudo sh cuda_11.0.2_450.51.05_linux.run
# 다시실행 continu 선택-> accept

$ vi ~/.bashrc #경로 설정하는 파일 열기 


# i를 사용해서 입력 가능 
# Esc 키 사용하여 파일 나간 후 Shift + : 을 누른 후 exit로 파일 종료 가능 

export PATH=/usr/local/cuda-11.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-11.0/lib64:$LD_LIBRARY_PATH

#경로 추가
source ~/.bashrc #변경된 부분 적용

$ nvcc --version 
# nvcc: NVIDIA (R) Cuda compiler driver
# Copyright (c) 2005-2020 NVIDIA Corporation
# Built on Thu_Jun_11_22:26:38_PDT_2020
# Cuda compilation tools, release 11.0, V11.0.194
# Build cuda_11.0_bu.TC445_37.28540450_0
```
#
## cuda 11.1 버전 설치
#

```bash
$ wget https://developer.download.nvidia.com/compute/cuda/11.1.0/local_installers/cuda_11.1.0_455.23.05_linux.run
$ sudo sh cuda_11.1.0_455.23.05_linux.run #다소 시간 걸림
```


-> Driver 제외하고 설치 (권장 드라이버 470이여서 따로 설치하는게 좋다고 함)

```bash
$ vi ~/.bashrc  

export PATH=/usr/local/cuda-11.1/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-11.1/lib64:$LD_LIBRARY_PATH
#경로추가

$ source ~/.bashrc
$ nvcc --version #확인
```


```bash
$ sudo apt install nvidia-driver-470 # 설치

$ sudo reboot # 재부팅

$ nvidia-smi # 확인
```

#
## pytorch 1.9.0 설치
#

https://pytorch.org/get-started/locally/

```bash
$ conda install pytorch torchvision torchaudio cudatoolkit=11.1 -c pytorch -c nvidia 
```
pytorch 설치 확인 명령어
```bash
$ python

import torch

print(torch.__version__) 
# 1.9.0
```

#
## mmcv-full 설치
#

https://mmcv.readthedocs.io/en/latest/get_started/installation.html

```bash
$ pip install mmcv-full -f https://download.openmmlab.com/mmcv/dist/cu111/torch1.9.0/index.html 
#conda를 deactivate 하고 설치시 오류가 발생함. mmcv-full 1.3.12 버전

$ conda activate #conda가 실행 되어 있지 않다면 실행후 설치.

```


```bash
$ conda create -n open-mmlab python=3.7 -y
$ conda activate open-mmlab

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
# checkpoints 폴더 생성 후 모델 다운로드 
$ mkdir checkpoints

$ wget https://download.openmmlab.com/mmdetection3d/v0.1.0_models/second/hv_second_secfpn_6x8_80e_kitti-3d-car/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth
```

```bash
# 예문 실행
$ python demo/pcd_demo.py demo/data/kitti/kitti_000008.bin configs/second/hv_second_secfpn_6x8_80e_kitti-3d-car.py checkpoints/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth
```

오류 발생

ValueError: numpy.ndarray size changed, may indicate binary incompatibility. Expected 88 from C header, got 80 from PyObject

nump 버전 1.19.0으로 변경
```bash
pip uninstall numpy
pip install numpy==1.19.0
```



