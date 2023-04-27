# Run the ROS2 OOD Demo on DB21M

## Preparetion
Run this command to install dependency.
```bash
pip3 install 'https://github.com/jetson-nano-wheels/python3.6-numpy-1.19.4/releases/download/v0.0.1/numpy-1.19.4-cp36-cp36m-linux_aarch64.whl'
pip3 install 'https://github.com/jetson-nano-wheels/python3.6-scipy-1.5.4/releases/download/v0.0.1/scipy-1.5.4-cp36-cp36m-linux_aarch64.whl'
```

## Camera Calibration 
Downoad 'camera_extrinsic' and copy to '/home/duckie/duckietown/config/calibrations/'. Change the configure file name according to your device name.
```bash
cd Downloads
git clone -b step5-Demo-OOD-Dectection https://github.com/GAO-XINWEI/Jetson_ROS.git
cp -r ~/Downloads/Jetson_ROS/camera_extrinsic/* /home/duckie/duckietown/config/calibrations/camera_extrinsic/
```

## Load Network
```bash
export ROBOT_OOD_DIR=~/duckietown/ood/
echo ${ROBOT_OOD_DIR}

```

## Run the Demo
```bash
cd ~
ros2 launch dt_demos vision_pipeline.launch.xml use_fake_camera:=false ood_detector:=true
```

## Show
```bash


```
