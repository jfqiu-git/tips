### 1. Update ubuntu kernel version to 3.16+ (4.4.0 rc6 wily is used now)
	
	$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc6-wily/linux-headers-4.4.0-040400rc6_4.4.0-040400rc6.201512202030_all.deb
	$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc6-wily/linux-headers-4.4.0-040400rc6-generic_4.4.0-040400rc6.201512202030_amd64.deb
	$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-rc6-wily/linux-image-4.4.0-040400rc6-generic_4.4.0-040400rc6.201512202030_amd64.deb
	$ sudo dpkg -i linux-headers-4.4.0-*.deb linux-image-4.4.0-*.deb

### 2. [Install Beignet](https://www.freedesktop.org/wiki/Software/Beignet/)

2.1 *Download [beignet 1.1.1 file](https://01.org/sites/default/files/beignet-1.1.1-source.tar.gz)*

2.2 *Install dependencies*

	$ sudo apt-get install cmake pkg-config python ocl-icd-dev ocl-icd-opencl-dev libdrm-dev libxfixes-dev libxext-dev llvm-3.5-dev clang-3.5 libclang-3.5-dev libtinfo-dev libedit-dev zlib1g-dev
	
2.3 *Build the Beignet*

	$ cd $Beignet_ROOT$
	$ mkdir build
	$ cd build
	$ make -j
	$ sudo make install

### 3. [Install libfreenect2](https://github.com/OpenKinect/libfreenect2/blob/master/README.md#linux)

3.1 *Install dependencies*

	$ git clone https://github.com/OpenKinect/libfreenect2.git
	$ cd libfreenect2
	$ cd depends; ./download_debs_trusty.sh
	$ sudo apt-get install build-essential cmake pkg-config
	$ sudo dpkg -i debs/libusb*deb
	$ sudo apt-get install libturbojpeg libjpeg-turbo8-dev
	$ sudo dpkg -i debs/libglfw3*deb; sudo apt-get install -f
	$ sudo dpkg -i debs/{libva,i965}*deb; sudo apt-get install -f
 
3.2 *Build*

	$ cd $libfreenect2_ROOT$
	$ mkdir build && cd build
	$ cmake .. -DCMAKE_INSTALL_PREFIX=$HOME/freenect2 -DENABLE_CXX11=ON
	$ make -j
	$ sudo make install
	
	$ sudo cp ../platform/linux/udev/90-kinect2.rules /etc/udev/rules.d/

3.3 *Test*

Replug the Kinect, then:
	$ ./bin/Protonect
	
### 4. Install [iai_kinect](https://github.com/code-iai/iai_kinect2)
	$ cd ~/catkin_ws/src
	$ git clone https://github.com/code-iai/iai_kinect2.git
	$ cd iai_kinect2
	$ rosdep install -r --from-paths .
	$ cd ~/catkin_ws
	$ catkin_make -DCMAKE_BUILD_TYPE="Release"

 	$ roslaunch kinect2_bridge kinect2_bridge.launch
