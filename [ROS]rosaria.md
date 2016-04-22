ROS Package [rosaria]

robot pioneer x3

- Install 
	>> git clone https://github.com/amor-ros-pkg/rosaria.git
	>> rosdep install rosaria
- Run the demo
	>> rosrun rosaria RosAria

- Give permission for ttyUSB0
	>> sudo vi /etc/udev/rules.d/70-ttyusb.rules
  and add
	KERNEL=="ttyUSB[0-9]*",MODE="0666" 

- Run the teleop
	>> rosrun turtlesim turtle_teleop_key
  or
	>> rostopic pub -1 /RosAria/cmd_vel geometry_msgs/Twist '[0.1, 0.0, 0.0]' '[0.0, 0.0, 0.0]'
