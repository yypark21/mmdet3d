# NCP
```bash
chmod go= aica_083_ftp.pem
ssh -i aica_083.pem ubuntu@address
```

# SECOND (multi gpu)
## train
```bash
./tools/dist_train.sh configs/second/hv_second_secfpn_6x8_80e_kitti-3d-car.py checkpoints/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth 2
```
## test
```bash
./tools/dist_test.sh configs/second/hv_second_secfpn_6x8_80e_kitti-3d-car.py checkpoints/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth 2
```

## checkpoint download
- original
```bash
wget https://download.openmmlab.com/mmdetection3d/v0.1.0_models/second/hv_second_secfpn_6x8_80e_kitti-3d-3class/hv_second_secfpn_6x8_80e_kitti-3d-3class_20200620_230238-9208083a.pth -P ./checkpoints/
```


# MVXNet (multi gpu)
https://github.com/open-mmlab/mmdetection3d/tree/master/configs/mvxnet
## train
```bash
./tools/dist_train.sh configs/mvxnet/dv_mvx-fpn_second_secfpn_adamw_2x8_80e_kitti-3d-3class.py --resume-from checkpoints/dv_mvx-fpn_second_secfpn_adamw_2x8_80e_kitti-3d-3class_20200621_003904-10140f2d.pth 2
```

## test
```bash
./tools/dist_test.sh configs/mvxnet/dv_mvx-fpn_second_secfpn_adamw_2x8_80e_kitti-3d-3class.py checkpoints/dv_mvx-fpn_second_secfpn_adamw_2x8_80e_kitti-3d-3class_20200621_003904-10140f2d.pth 2
```

## checkpoint download
- original
```bash
wget https://download.openmmlab.com/mmdetection3d/v0.1.0_models/mvxnet/dv_mvx-fpn_second_secfpn_adamw_2x8_80e_kitti-3d-3class/dv_mvx-fpn_second_secfpn_adamw_2x8_80e_kitti-3d-3class_20200621_003904-10140f2d.pth -P ./checkpoints/
```


# commands
## frequently used
1. dataset preparation
```bash
python tools/create_data.py kitti --root-path ./data/kitti --out-dir ./data/kitti --extra-tag kitti
```

2. train
```bash
python tools/train.py configs/second/hv_second_secfpn_6x8_80e_kitti-3d-car.py --resume-from checkpoints/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth
```

3. test
```bash
python tools/test.py configs/second/hv_second_secfpn_6x8_80e_kitti-3d-car.py checkpoints/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth --show --show-dir data/kitti/show_dir/
```
- mAP only
```bash
python tools/test.py configs/second/hv_second_secfpn_6x8_80e_kitti-3d-car.py checkpoints/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth --eval mAP
```

4. browse
```bash
python tools/misc/browse_dataset.py configs/mvxnet/dv_mvx-fpn_second_secfpn_adamw_2x8_80e_kitti-3d-3class.py --task multi_modality-det --output-dir data/kitti/results/ --online
```

5. visualization
- prediction results (Car class only)
```bash
python tools/test.py configs/second/hv_second_secfpn_6x8_80e_kitti-3d-car.py checkpoints/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth --show --show-dir data/kitti/show_dir/
```

## demo
1. checkpoint download
```bash
mkdir checkpoints
wget https://download.openmmlab.com/mmdetection3d/v0.1.0_models/second/hv_second_secfpn_6x8_80e_kitti-3d-car/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth -P ./checkpoints/
```
2. run demo
```bash
python demo/pcd_demo.py demo/data/kitti/kitti_000008.bin configs/second/hv_second_secfpn_6x8_80e_kitti-3d-car.py checkpoints/hv_second_secfpn_6x8_80e_kitti-3d-car_20200620_230238-393f000c.pth --show
```



## Sample download
```bash
pip install gdown
```

### download kitti dataset sample to data/kitti/ directory
- kitti 40 (overwrite)
```bash
rm -rf data/kitti
mkdir data/tmp
gdown https://drive.google.com/uc?id=1_3yU3HmFf-SqBrXXJLZw8-a_k7E6LV_D -O data/tmp/kitti.zip
unzip data/tmp/*.zip -d data/ && rm -rf data/tmp
```
- kitti 3 (overwrite)
```bash
rm -rf data/kitti
mkdir data/tmp
gdown https://drive.google.com/uc?id=1rXb4RPC1ZclLlfKWLUppW71iKXvTFIEB -O data/tmp/kitti.zip
unzip data/tmp/*.zip -d data/ && rm -rf data/tmp
```

### kitti dataset structure
```
trainval                 test
   |                      |
   +-----------+          |
   |           |          |
train(50%)  val(50%)     test
```

# docker env
```bash
sudo docker run --gpus all --shm-size=8g -it -v /home/s/dev/mmdetection3d/data:/mmdetection3d/data mmdetection3d
```
```bash
apt-get update
apt-get install wget
apt-get install vim
```
