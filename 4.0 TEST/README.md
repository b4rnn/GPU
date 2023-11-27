```
#include <iostream>
using namespace std;

#include <opencv2/core.hpp>
using namespace cv;

#include <opencv2/cudaarithm.hpp>
using namespace cv::cuda;

int main()
{
    std::cout << cv::getBuildInformation() << std::endl; 
    cv::cuda::setDevice(0);
    printShortCudaDeviceInfo(getDevice());
    int cuda_devices_number = getCudaEnabledDeviceCount();
    cout << "CUDA Device(s) Number: "<< cuda_devices_number << endl;
    DeviceInfo _deviceInfo;
    bool _isd_evice_compatible = _deviceInfo.isCompatible();
    cout << "CUDA Device(s) Compatible: " << _isd_evice_compatible << endl;
    return 0;
}
```

#SWITCH CUDA VERSION
export PATH=/usr/local/cuda-10.4/bin${PATH:+:$PATH}
export LD_LIBRARY_PATH=/usr/local/cuda-10.4/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
source ~/.bashrc
#CHECK CUDNN VERSION
cat /usr/local/cuda/include/cudnn_version.h | grep CUDNN_MAJOR -A 2
