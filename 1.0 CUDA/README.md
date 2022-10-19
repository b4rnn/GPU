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
# CUDA_ARCH_BIN
```
git clone https://github.com/NVIDIA-AI-IOT/deepstream_tlt_apps.git
cd deepstream_tlt_apps/TRT-OSS/x86
nvcc deviceQuery.cpp -o deviceQuery
./deviceQuery | grep Capability
```
