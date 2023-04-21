# Install Torch on Jetson Nano
Install torch following the instruction [here](https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048). Notice that you many face many different package installation error caused by incompatible version of package, e.g. 'libnuma1', 'libnuma-dev', 'libhwloc-dev', 'libibverbs-dev' and 'tensorrt'. Try to install and uninstall them depending on the errors you faced.


## Install Torch
```bash
wget https://nvidia.box.com/shared/static/p57jwntv436lfrd78inwl7iml6p13fzh.whl -O torch-1.8.0-cp36-cp36m-linux_aarch64.whl
sudo apt-get install python3-pip libopenblas-base libopenmpi-dev libomp-dev
pip3 install Cython
pip3 install numpy torch-1.8.0-cp36-cp36m-linux_aarch64.whl
```

## Install Torchvision
```bash
sudo apt-get install libjpeg-dev zlib1g-dev libpython3-dev libavcodec-dev libavformat-dev libswscale-dev
git clone --branch v0.9.0 https://github.com/pytorch/vision torchvision
cd torchvision
export BUILD_VERSION=0.9.0
python3 setup.py install --user
```

## Appendix
Notice that the relationship between Torch and Torchvision should be following:
```bash
    PyTorch v1.0 - torchvision v0.2.2
    PyTorch v1.1 - torchvision v0.3.0
    PyTorch v1.2 - torchvision v0.4.0
    PyTorch v1.3 - torchvision v0.4.2
    PyTorch v1.4 - torchvision v0.5.0
    PyTorch v1.5 - torchvision v0.6.0
    PyTorch v1.6 - torchvision v0.7.0
    PyTorch v1.7 - torchvision v0.8.1
    PyTorch v1.8 - torchvision v0.9.0
    PyTorch v1.9 - torchvision v0.10.0
    PyTorch v1.10 - torchvision v0.11.1
    PyTorch v1.11 - torchvision v0.12.0
    PyTorch v1.12 - torchvision v0.13.0
```
