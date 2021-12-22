# Docker setup

## Environment
-   OS: Ubuntu 18.04
-   GPU: NVIDIA GeForce RTX 2070 SUPER

## Install
1. install docker
```bash
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world
```
2. install nvidia-container-toolkit install
```bash
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update && sudo apt-get install -y nvidia-container-toolkit
sudo systemctl restart docker
```
3. install conda and activate env
4. build
```bash
docker build -t mmdetection3d docker/
```
```bash
apt-get update
apt-get install wget
```
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
