ROS Package [hokuyo]

http://wiki.ros.org/hokuyo_node/Tutorials

- Install packege
	>> sudo apt-get install ros-indigo-hokuyo-node

- Look up devices
	>> ls -l /dev/ttyACM0

- Configuring the hokuyo
	>> sudo chmod a+rw /dev/ttyACM0
  or 
	>> sudo gedit /etc/udev/rules.d/80-ttyACM.rules
  and add
 	KERNEL=="ttyACM[0-9]*",MODE="0666"
	KERNEL=="ttyACM[0-9]*", ACTION=="add", ATTRS{idVendor}=="15d1", MODE="0666", GROUP="dialout", PROGRAM="/opt/ros/indigo/env.sh rosrun hokuyo_node getID %N q", SYMLINK+="sensors/hokuyo_%c"

- Run the demo
	>> rosrun hokuyo_node hokuyo_node


http://blog.csdn.net/zyh821351004/article/details/41577105
