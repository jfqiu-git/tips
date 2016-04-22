- Install Gazebo
  hint: ros-indigo is compabined with gazebo 2.* version.
	>> sudo apt-get install -y gazebo2
  Before attempting to install the gazebo_ros_pkgs, make sure the stand-alone Gazebo works by running in terminal:
	>> gazebo
  and test that you have the right version of Gazebo

- Install gazebo-ros-pkgs
	indigo
	>> sudo apt-get install ros-indigo-gazebo-ros-pkgs ros-indigo-gazebo-ros-control

- Testing Gazebo with ROS Integration
	>> source opt/ros/indigo/setup.bash
	>> source ~/catkin_ws/devel/setup.bash
	>> rosrun gazebo_ros gazebo
  Additionally, we can start Gazebo using roslaunch
	>> roslaunch gazebo_ros empty_world.launch