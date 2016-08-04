# Instruction on Installing Caffe (Ubuntu 14.04 x64 GTX980Ti)

----

    I have successfully compiled and run Caffe on Clean Ubuntu 14.04 LTS (64bit) as following.
## Step 1. Install dependencies
[Reference](http://caffe.berkeleyvision.org/install_apt.html).
```
$ sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler
$ sudo apt-get install --no-install-recommends libboost-all-dev
$ sudo apt-get install libatlas-base-dev
$ sudo apt-get install python-dev
$ sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev
$ sudo apt-get install g++
$ sudo apt-get install git
$ sudo apt-get install freeglut3-dev
```
## Step 2. Install CUDA library
    CUDA is only required to GPU-mode, this step can be skipped for CPU-only installation. CUDA library version 7.0 and the latest driver version are recommended. Because the driver bundled with the library is usually out-of-date, so we need to Install the **CUDA library** and **latest driver** separately.

    CUDA library** installation referenced to [NVIDIA CUDA Getting Started Guide for Linux](https://developer.nvidia.com/cuda-downloads/).

###1. Disable the Nouveau drivers :
* Create a file at **/etc/modprobe.d/blacklist-nouveau.conf** with the following contents : 
```
blacklist nouveau
options nouveau modeset=0
```
* Regenerate the kernel initramfs : 
```
$ sudo update-initramfs –u
```
*  Reboot computer 
*  Confirm this works if the following command prints nothing :
```
$ lsmod | grep nouveau
```
###2. Download runfile
Choose the suitable [runfile](https://developer.nvidia.com/cuda-downloads/)  for your installation. (I got **cuda_7.0.28_linux.run** for myself).
###3. Install CUDA library
* Press *Ctrl + alt + F3* to enter the text mode, and type these command: 
``` 
$ chmod +x cuda_7.0.28_linux.run
$ sudo stop lightdm
$ sudo sh cuda_7.0.28_linux.run
```
* Press *Enter* until 100%, and Choose **“yes”** all the way except : 
> **Notice: Install NVIDIA Accelerate Graphic driver ? Choose "NO" !**

###4. Restart the desktop :
```
$ sudo start lightdm
```
###5. Configure environment :
```
$ export PATH=/usr/local/cuda-7.0/bin:$PATH
$ export LD_LIBRARY_PATH=/usr/local/cuda-7.0/lib64:$LD_LIBRARY_PATH
$ sudo ldconfig /usr/local/cuda/lib64
```

## Step 3. Install NVIDIA latest driver
    I have a GTX980Ti, but the driver bundled with the CUDA 7.0 is version 346.46, the 346.46 driver probably doesn't recognize GTX980Ti! So we need to install the latest driver now.
[Choose driver for your graphic card](http://www.geforce.cn/drivers)
```
$ sudo sh NVIDIA-Linux-x86_64-352.21.run
```
"**Accept**" all the way will be OK.

Verified by :
```
$ cd NVIDIA_CUDA-7.0_Samples
$ make –j12
$ ./bin/deviceQuiry
```
If print "**PASS**", CUDA library and NVIDIA driver have been installed correctly.

## Step 4. Install OpenCV
```
$ git clone https://github.com/jayrambhia/Install-OpenCV.git 
$ cd Install-OpenCV/Ubuntu
$ ./dependencies
$ cd 2.4
$ ./opencv2_4_10.sh
```
## Step 5. Caffe Compilation
```
$ cp Makefile.config.example Makefile.config
```
    I have a CPU I7-5930K, 6 cores 12 threads.
```
$ cd $CAFFE_ROOT$
$ mkdir build
$ cd build
$ cmake .. -DCMAKE_BUILD_TYPE=Release
$ make –j12
$ sudo make install
```
## Step 6. Interface (pycaffe)
    In order to use pycaffe properly we need to install these libraries :
```
$ sudo apt-get install python-numpy python-scipy python-matplotlib python-sklearn python-skimage python-h5py python-protobuf python-leveldb python-networkx python-nose python-pandas python-gflags Cython ipython 
```

## Step 7. Implement Caffe to your project
    There is a *CMakeLists.txt* example, confirm that you have followed the **Step 5**  in this tutorial. 
```
cmake_minimum_required(VERSION 2.8)
project(caffe_test)

find_package(OpenCV REQUIRED)
find_package(Caffe REQUIRED)

include_directories(${Caffe_INCLUDE_DIRS})
add_definitions(${Caffe_DEFINITIONS})

add_executable(caffe_test src/caffe_test.cpp)
target_link_libraries(caffe_test ${OpenCV_LIBS} ${Caffe_LIBRARIES})
```
## Debug 
### pycaffe related
* **ImportError: No module named _caffe**
Remember to import caffe from root_path :
```
#Add root_path 
caffe_root = '../../' 
sys.path.insert(0, caffe_root + 'python')

import caffe
```
* **ImportError: No module named _lmdb**
Install lmdb from *apt* or *pip* :
```
$ sudo apt-get install liblmdb-dev
```
```
$ sudo apt-get install python-pip
$ sudo pip install lmdb
```
### cuda error
* Check failed: error == cudaSuccess (2 vs. 0)  out of memory
*** Check failure stack trace: ***
Maybe snapshot path error.

### Loss cannot deverge
* weights maybe some layers be zero or num_output incorrect. Add :
```
convolution_param{
  weight_filler {
    type: "xavier"
  }
  bias_filler {
    type: "constant"
  }
}
```

### FCN-32 training 
* Google group [Fully convolutional neural net 'Youssef Kashef' 15/9/17]
* fcn-32s train road 3 classes, 50000 iteration, test_iter must be the size of batch of val-data, loss deverge to 5000
* fcn-32s train traffic 2 classes,  iteration, test_iter must be the size of batch of val-data, loss deverge to 
