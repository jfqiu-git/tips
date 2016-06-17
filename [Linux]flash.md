### Download file
	Go to Adobe's Flash Player download page. save the file (i.e. install_flash_player_"version"_linux."processor".tar.gz).

### Extract files
	>> cd /home/user/Downloads
	Extract libflashplayer.so from the file you downloaded with the command tar -zxvf install_flash_player_"version"_linux."processor".tar.gz.

### Copy files
	As the super user, copy the extracted file, libflashplayer.so, to your Firefox installation directory's plugins sub-directory. For example, if Firefox is installed in /usr/lib/mozilla, use the command sudo cp libflashplayer.so /usr/lib/mozilla/plugins and then enter your super user password when prompted. 
