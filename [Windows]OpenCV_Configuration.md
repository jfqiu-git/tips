### Configure Environment
1. 添加用户变量

	OPENCVROOT [D:\opencv2411\opencv]

2. 添加path变量

	;%OPENCVROOT%\build\x64\vc12\bin;

3. 程序中添加配置文件

* 先转换为Release x64项目，接着在属性管理器中的Release x64中添加配置文件

* C++ - 附加包含目录：
	$(OPENCVROOT)\build\include\

* 链接器 - 常规 - 附加库目录：
	$(OPENCVROOT)\build\x64\vc12\lib\

* 链接器 - 输入 - 附加依赖项：

	opencv_contrib2411.lib
	opencv_core2411.lib
	opencv_features2d2411.lib
	opencv_flann2411.lib
	opencv_gpu2411.lib
	opencv_highgui2411.lib
	opencv_imgproc2411.lib
	opencv_legacy2411.lib
	opencv_ml2411.lib
	opencv_nonfree2411.lib
	opencv_objdetect2411.lib
	opencv_ocl2411.lib
	opencv_photo2411.lib
	opencv_stitching2411.lib
	opencv_superres2411.lib
	opencv_ts2411.lib
	opencv_video2411.lib
	opencv_videostab2411.lib
