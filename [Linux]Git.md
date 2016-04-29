### 安装 Git
	sudo apt-get install git

### 设置 config
	$ git config --global user.name "jfqiu-git"
	$ git config --global user.email jfqiu_bit@126.com
	$ git config --global core.editor vim
	$ git config --global color.ui true
### 创建 SSH Key
	$ ssh-keygen -t rsa -C "jfqiu_bit@126.com"
	"Account settings:, 在Key文本框里粘贴id_rsa.pub文件的内容

### 使用git在本地创建一个项目的过程

	$ mkdir ~/hello-world    //创建一个项目hello-world
	$ cd ~/hello-world       //打开这个项目
	$ git init               //初始化 
	$ touch README
	$ git add README                   //更新README文件
	$ git commit -m 'first commit'     //提交更新，并注释信息“first commit”
	$ Create a New Repository on GitHub //创建一个新的仓库
	$ git remote add origin git@github.com:jfqiu-git/hello-world.git     //连接远程github项目  
	$ git push -u origin master        //将本地项目更新到github项目上去

	$ git pull --rebase origin master

### 创建dev分支，然后切换到dev分支
	$ git branch dev
	$ git checkout dev

	$ git branch
