1. 右键点击打算共享的文件夹，并选择“Local Network Share（本地网络共享）”; 如果在右键菜单中看不到“Local Network Share”的选项:
```
sudo apt-get install nautilus-share
```
然后重启Nautilus:
```
nautilus -q
```

2. 选中“Share this folder（共享该文件夹）”与“Guest access（访客权限）”

3. Windows中输入“\\$IP” 即可
