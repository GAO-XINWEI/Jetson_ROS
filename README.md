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

## GPIO Permission ERROR (Ignore if no error)
1. Follow [this website](https://forums.developer.nvidia.com/t/there-is-no-99-gpio-rules-file-in-the-latest-jetson-gpio-library/118619) to move '99-gpio.rules' files into folder.
2. Follow [thiswebsite](https://maker.pro/nvidia-jetson/tutorial/how-to-use-gpio-pins-on-jetson-nano-developer-kit) to '' setup GPIO. Please try to uninstall 'sudo pip3 install Jetson.GPIO' if not working, since GPIO is inbuilt in Jetson Nano system.

## OpenCV Gstreamer ERROR (Ignore if no error)
Reinstall OpenCV on Jetson Nano following [this](https://www.youtube.com/watch?v=3QYayL5y2hk).

## Run the Demo
```bash
cd ~
ros2 launch dt_demos vision_pipeline.launch.xml use_fake_camera:=false ood_detector:=true
```

## Show
```bash
# On your local computer
rqt_graph
```
