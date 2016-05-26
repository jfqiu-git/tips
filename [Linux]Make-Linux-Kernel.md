### Download kernel
	>> wget https://www.kernel.org/pub/linux/kernel/v3.0/linux-3.19.8.tar.gz

### Copy & Tar
	>> sudo cp linux-3.19.8.tar.gz /usr/src/
	>> cd /usr/src/
	>> sudo tar zxvf linux-3.19.8.tar.gz
	>> cd linux-3.19.8

### Install libncurses
	>> sudo apt-get install libncurses-dev

### Config kernel
	>> make mrproper
	>> sudo make menuconfig (Use default)

### Build Kernel
	>> sudo make all -j4 (Build kernel & modules)
	>> sudo make modules_install
	>> sudo make install

### Grub gedit 
	>> sudo update-grub
	>> sudo reboot
