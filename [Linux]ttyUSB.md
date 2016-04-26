Ubuntu [ttyUSB permission]

- Enable the permission for hokuyo by 	
	>> sudo vi /etc/udev/rules.d/70-ttyusb.rules
  and add
	>> KERNEL=="ttyUSB[0-9]*",MODE="0666" 

or


crw-rw---- 1 root dialout ... /dev/ttyS0
sudo adduser $USER dialout
