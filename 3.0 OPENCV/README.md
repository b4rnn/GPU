```
/sbin/ldconfig -N -v $(sed ‘s/:/ /’ <<< $LD_LIBRARY_PATH) 2>/dev/null | grep libcudnn
```
```
cd /tmp
wget -O opencv.zip https://github.com/opencv/opencv/archive/opencv-4.5.2.zip
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/opencv-4.5.2.zip
unzip opencv.zip
unzip opencv_contrib.zip
# Create build directory and switch into it
mkdir -p build && cd build
#build opencv with dnn modules and cuda support
cmake -D CMAKE_BUILD_TYPE=RELEASE  -D CMAKE_C_COMPILER=/usr/bin/gcc-7  -D CMAKE_INSTALL_PREFIX=/usr/local  -D BUILD_TIFF=ON  -D WITH_FFMPEG=ON  -D WITH_GSTREAMER=ON  -D WITH_TBB=ON -D BUILD_TBB=ON -D WITH_EIGEN=ON -D WITH_V4L=ON -D WITH_LIBV4L=ON -D WITH_VTK=OFF -D WITH_QT=OFF -D ENABLE_FAST_MATH=1 -D CUDA_FAST_MATH=1 -D WITH_CUBLAS=1 -D WITH_OPENGL=ON -D OPENCV_ENABLE_NONFREE=ON -D INSTALL_C_EXAMPLES=OFF -D INSTALL_PYTHON_EXAMPLES=OFF -D PYTHON_DEFAULT_EXECUTABLE=$(which python3) -D BUILD_SHARED_LIBS=OFF -D BUILD_NEW_PYTHON_SUPPORT=ON -D OPENCV_GENERATE_PKGCONFIG=ON -D BUILD_TESTS=OFF -D WITH_CUDA=ON -D WITH_CUDNN=ON -D OPENCV_DNN_CUDA=ON -D CUDA_ARCH_BIN=6.1 -D ENABLE_FAST_MATH=ON -D CUDA_FAST_MATH=ON -D WITH_CUBLAS=ON -D OPENCV_PC_FILE_NAME=opencv4.pc -D CUDNN_INCLUDE_DIR=/usr/local/cuda-11.4/targets/x86_64-linux/include/ -D CUDNN_LIBRARY=/usr/lib/x86_64-linux-gnu/libcudnn.so.8.2.4 -D CUDNN_VERSION=8.2.4  -D OPENCV_EXTRA_MODULES_PATH=/tmp/opencv_contrib-4.5.2/modules ..
```
```
make -j$(nproc)
sudo make install
sudo ldconfig
pkg-config --modversion opencv4
```
