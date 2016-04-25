### Download g2o
	>> git clone https://github.com/RainerKuemmerle/g2o

### Install dependencies
	>> sudo apt-get install libeigen3-dev libsuitesparse-dev libqt4-dev qt4-qmake

### Handle "libqglviewer-qt4-dev"
	* "libqglviewer-qt4-dev" is not fine with Ubuntu 14.04;
	* Unpack "libqglviewer_for_ubuntu1404.tar.gz"
	* >> sudo dpkg -i libqglviewer-dev-common_2.3.4-4ubuntu2_all.deb
	* >> sudo dpkg -i libqglviewer-qt4-2_2.3.4-4ubuntu2_amd64.deb 
	* >> sudo dpkg -i libqglviewer-qt4-dev_2.3.4-4ubuntu2_amd64.deb

	if conflict or break, sudo apt-get remove it

### Install g2o [https://github.com/RainerKuemmerle/g2o/issues/53]
	* >> ccmake ..
	* click "c" to configure
	* Enable "BUILD_CSPARSE"
	* 




