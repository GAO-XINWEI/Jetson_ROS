# Run the ROS2 OOD Demo on DB21M

## Preparetion
Run this command to install dependency.
```bash
pip install 'https://github.com/jetson-nano-wheels/python3.6-numpy-1.19.4/releases/download/v0.0.1/numpy-1.19.4-cp36-cp36m-linux_aarch64.whl'
pip install 'https://github.com/jetson-nano-wheels/python3.6-scipy-1.5.4/releases/download/v0.0.1/scipy-1.5.4-cp36-cp36m-linux_aarch64.whl'
```

## Camera Calibration 
Downoad 'camera_extrinsic' and copy to '/home/duckie/duckietown/config/calibrations/'

```bash
cd Downloads
git clone https://github.com/GAO-XINWEI/Jetson_ROS.git
unzip Jetson_ROS.zip
cp -r ~/Downloads/Jetson_ROS/camera_extrinsic/* /home/duckie/duckietown/config/calibrations/camera_extrinsic/
```


## Run the Demo
```bash
ros2 launch dt_demos vision_pipeline.launch.xml use_fake_camera:=false ood_detector:=true
```
