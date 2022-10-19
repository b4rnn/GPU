* DEPENDENCIES
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
```
# CUDA_ARCH_BIN
```
git clone https://github.com/NVIDIA-AI-IOT/deepstream_tlt_apps.git
cd deepstream_tlt_apps/TRT-OSS/x86
nvcc deviceQuery.cpp -o deviceQuery
./deviceQuery | grep Capability
```
