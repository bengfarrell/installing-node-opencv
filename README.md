installing-node-opencv
======================

instructions for installing Node OpenCV


Windows
=======

1. Download OpenCV:
-------------------

http://sourceforge.net/projects/opencvlibrary/files/opencv-win/2.3.1/OpenCV-2.3.1-win-superpack.exe/download

Extract and move files anywhere, I prefer just puttin them on my C: root in a folder called "opencv"


2. Download GTK All in One Bundle
---------------------------------

http://win32builder.gnome.org/gtk+-bundle_3.6.4-20131201_win64.zip

Extract and move files anywhere, I prefer just puttin them on my C: root in a folder called "gtk"

This contains things you need like pkg-config, libg, and more (seemingly even installing these components one by one may not cut it)

Note: The above link is for 64bit, if you are running 32bit, find the other bundle


2. Add Environmental Variables:
-------------------------------

Variable name: OPENCV_DIR

Variable value: C:\opencv\build\x64\vc10

Note: value is where you put the "opencv" folder in step 1
Note: have the x86 version of node? Use \build\x86 instead



3. Install Microsoft Visual Studio Express 2010
------------------------------------------------

(why 2010? OpenCV 2.3.1 only has libs for 2010...vc10 is VS 2010)





