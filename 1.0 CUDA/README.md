# DEPENDENCIES
*
    `Ubuntu 18.04 LTS`
    `NVIDIA 470`
    `CUDA 11.04`
    `CuDNN 7.6.5`
    `gcc/g++ 11.1.0`
# SETUP
```
 sudo apt-get remove --purge '^cuda-.*'
 sudo apt-get remove --purge '^nvidia-.*'
 sudo apt-get remove --purge '^libnvidia-.*'
 sudo rm -rf .X0-lock
 sudo apt-get update
 sudo apt install nvidia-driver-470
 wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-ubuntu1804.pin
 sudo mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
 wget https://developer.download.nvidia.com/compute/cuda/11.4.2/local_installers/cuda-repo-ubuntu1804-11-4-local_11.4.2-470.57.02-1_amd64.deb
 sudo dpkg -i cuda-repo-ubuntu1804-11-4-local_11.4.2-470.57.02-1_amd64.deb
 sudo apt-key add /var/cuda-repo-ubuntu1804-11-4-local/7fa2af80.pub
 sudo apt-get update
 sudo apt-get -y install cuda
```

# PATH 
```
sudo nano ~/.profile
```
```
if [ -d "/usr/local/cuda-11.4/bin/" ]; then
    export PATH=/usr/local/cuda-11.4/bin${PATH:+:${PATH}}
    export LD_LIBRARY_PATH=/usr/local/cuda-11.4/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
fi
```
```
source ~/.profile
```
# reboot
```
sudo system restart
```
# nvidia-smi
```
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 470.57.02    Driver Version: 470.57.02    CUDA Version: 11.4     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  On   | 00000000:2D:00.0  On |                  N/A |
|  0%   46C    P8    23W / 370W |    205MiB / 12046MiB |      1%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      1362      G   /usr/lib/xorg/Xorg                 14MiB |
|    0   N/A  N/A      1509      G   /usr/bin/gnome-shell               64MiB |
|    0   N/A  N/A      3727      G   /usr/lib/xorg/Xorg                 58MiB |
|    0   N/A  N/A      3862      G   /usr/bin/gnome-shell               64MiB |
+-----------------------------------------------------------------------------+
```
# nvcc -V
```
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2021 NVIDIA Corporation
Built on Sun_Aug_15_21:14:11_PDT_2021
Cuda compilation tools, release 11.4, V11.4.120
Build cuda_11.4.r11.4/compiler.30300941_0
```
# CUDA_ARCH_BIN
```
git clone https://github.com/NVIDIA-AI-IOT/deepstream_tlt_apps.git
cd deepstream_tlt_apps/TRT-OSS/x86
nvcc deviceQuery.cpp -o deviceQuery
./deviceQuery | grep Capability
```
```
CUDA Capability Major/Minor version number:    8.6
```
