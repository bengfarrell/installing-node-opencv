installing-node-opencv
======================

instructions for installing Node OpenCV


Windows 8.1
===========

1. Download OpenCV:
-------------------

http://sourceforge.net/projects/opencvlibrary/files/opencv-win/2.3.1/OpenCV-2.3.1-win-superpack.exe/download

Extract and move files anywhere, I prefer just puttin them on my C: root in a folder called "opencv"


2. Copy OpenCV.pc:
-------------------

There's a config file of sorts called opencv.pc hosted here on this repo. I stole it from https://github.com/notcoffeetable/node-opencv
This file will provide some pointers to the various opencv libraries. Be sure to edit this file if you placed OpenCV at a different location other than
C:\opencv. After or before editing, move the file to C:\opencv. It doesn't need to be here, but I thought it would make sense to put OpenCV related files here. In step 3b,
you'll add an environmental variable to point to this location. If you place the file in a different folder, be sure to make note of this when you progress to step 3b.

Note: I am using 64bit Windows and 64bit Node.js. My "libdir" variable in this file reflects this location /bin/x64/vc10. If you are using x86, be sure to update this location.
Also be sure to make this location and the environmental var location in step 3a match as they both rely on the files here.


2. Download GTK All in One Bundle
---------------------------------

http://win32builder.gnome.org/gtk+-bundle_3.6.4-20131201_win64.zip

Extract and move files anywhere, I prefer just puttin them on my C: root in a folder called "gtk"

This contains things you need like pkg-config, libg, and more (seemingly even installing these components one by one may not cut it)

Note: The above link is for 64bit, if you are running 32bit, find the other bundle


3a. Add Environmental Variables:
--------------------------------

Variable name: OPENCV_DIR

Variable value: C:\opencv\build\x64\vc10

Note: value is where you put the "opencv" folder in step 1
Note: have the x86 version of node? Use \build\x86 instead


3b. Add Environmental Variables:
--------------------------------

Variable name: PKG_CONFIG_PATH

Variable value: C:\opencv

Note: value is where you put the "opencv.pc" file in step 2



4. Add a PATH entry:
-------------------------------

Variable name: PATH

Add to path: C:\gtk\bin

Here you're adding whatever's in gtk\bin to the system path, so you can use all the libraries in bin like libg, pkg-config, etc

Note: value is where you put the "gtk" folder in step 2




5. Install Microsoft Visual Studio Express 2013
------------------------------------------------

you need the MSVS Build tools




6. NPM Install opencv
---------------------------------------------

npm install --save-dev --msvs_version=2013

For some reason, npm falls back to defaulting to the VS2010 tools, which probably don't exist on your machine




