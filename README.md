installing-node-opencv
======================

instructions for installing Node OpenCV


Windows
=======

1. Download OpenCV:
-------------------

http://sourceforge.net/projects/opencvlibrary/files/opencv-win/2.3.1/OpenCV-2.3.1-win-superpack.exe/download

Extract and move files anywhere, I prefer just puttin them on my C: root in a folder called "opencv"


2. Download pkg-config:
-------------------

http://pkgconfig.freedesktop.org/releases/pkg-config-0.28.tar.gz

Extract and move files anywhere, I prefer just puttin them on my C: root in a folder called "pkg-config"


2. Add Environmental Variables:
-------------------------------

Variable name: OPENCV_DIR

Variable value: C:\opencv\build\x64\vc10

Note: value is where you put the "opencv" folder in step 1
Note: have the x86 version of node? Use \build\x86 instead



3. Install Microsoft Visual Studio Express 2010
------------------------------------------------

(why 2010? OpenCV 2.3.1 only has libs for 2010...vc10 is VS 2010)





