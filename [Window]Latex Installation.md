### Install CTex 

### Install TexStudio

#### Texstudio--选项--设置--编辑器--默认字体编码--GB2312
#### Texstudio--编辑--设置编码--GB2312--文件重新加载

### pdf目录乱码问题
  编写一个新的bat脚本：
    for /f "delims=" %%a in ('DIR *.out /B') do gbk2uni %%~na.out &pdflatex %%~na.tex
