# Example for Gitlab

1. First, add new "Group", add new "members";
2. Second, add new "Repository";

### Git global setup

	$ git config --global user.name "邱凡"
	$ git config --global user.email "jfqiu_bit@126.com"

### Create a new repository

	$ git clone http://10.106.18.86/BankRobot/facedt.git
	$ cd facedt
	$ touch README.md
	$ git add README.md
	$ git commit -m "add README"
	$ git push -u origin master

### Existing folder or Git repository

	$ cd existing_folder
	$ git init
	$ git remote add origin http://10.106.18.86/BankRobot/facedt.git
	$ git add .
	$ git commit
	$ git push -u origin master

