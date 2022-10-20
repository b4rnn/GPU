```
/sbin/ldconfig -N -v $(sed ‘s/:/ /’ <<< $LD_LIBRARY_PATH) 2>/dev/null | grep libcudnn
whereis cudnn.h
cudnn: /usr/include/cudnn.h
download cudnn-11.4-linux-x64-v8.2.4.15.tgz
tar -zxf cudnn-11.4-linux-x64-v8.2.4.15.tgz
cd cuda
sudo cp cuda/include/cudnn*.h /usr/local/cuda-11.4/include  
sudo cp cuda/lib64/libcudnn* /usr/local/cuda-11.4/lib64  
sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda-11.4/lib64/libcudnn*
```
