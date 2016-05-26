### IP
## COMPUTER1
	- IP"192.168.1.1"
	- MASK"255.255.255.0"
## COMPUTER2
	- IP"192.168.1.2"
	- MASK"255.255.255.0"

### ROSURI
## COMPUTER1
	- hostname
	- gedit ~/.bashrc
	- export ROS_HOSTNAME=computer1_hostname
	- export ROS_MASTER_URI=http://computer1_hostname:11311

## COMPUTER2
	- hostname
	- gedit ~/.bashrc
	- export ROS_HOSTNAME=computer2_hostname 
	- export ROS_MASTER_URI=http://computer1_hostname:11311

### ROSNAME
	- sudo chmod a+w /etc/hosts
	- vim /etc/hosts
		127.0.0.1   localhost
		127.0.1.1   inin-bit
		192.168.1.1 computer1_hostname
		192.168.1.2 computer2_hostname
	- sudo /etc/init.d/networking restart

### TEST
## COMPUTER1
	- roscore
	- rosrun turtlesim turtlesim_node

## COMPUTER2
	- rosrun turtlesim draw_square
