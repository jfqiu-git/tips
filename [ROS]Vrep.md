## Installation ROS Indigo

## Installation V-Rep
	* Go to http://www.coppeliarobotics.com/, and download 3.2.2
	* unzip it
	* >> ./vrep.sh

## Installation Plugin
	* >> cd catkin_ws/src
	* >> git clone https://github.com/lagadic/vrep_ros_bridge.git
	* >> gedit ~/.bashrc
	* add "export VREP_ROOT_DIR=/ChangeWithyourPathToVrep/"
	* >> catkin_make
	* Go to Vrep root directory
	* >> ln -s /YOUR_CATKIN_WS_PATH/devel/lib/libv_repExtRosBridge.so
