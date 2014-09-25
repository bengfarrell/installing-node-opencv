installing-node-opencv
======================

instructions for installing Node OpenCV


Windows 8.1
===========

1. Download OpenCV:
-------------------

http://opencv.org/downloads.html

Download version 2.4.9

(please note that I've tried 2.3.1 as mentioned in the official node-opencv repo, however, though I've been able to compile it,
the DLLs don't seem to work. I speculate that it may be a VS2013 vs VS2010 compile issue, as we are using the vc12 DLL files.
Hopefully there are no negative implications when using node-opencv with this newer version)

Extract and move files anywhere, I prefer just puttin them on my C: root in a folder called "opencv"


2. Copy OpenCV.pc:
-------------------

There's a config file of sorts called opencv.pc hosted here on this repo. I stole it from https://github.com/notcoffeetable/node-opencv
This file will provide some pointers to the various opencv libraries. Be sure to edit this file if you placed OpenCV at a different location other than
C:\opencv. After or before editing, move the file to C:\opencv. It doesn't need to be here, but I thought it would make sense to put OpenCV related files here. In step 3b,
you'll add an environmental variable to point to this location. If you place the file in a different folder, be sure to make note of this when you progress to step 3b.

Note: I am using 64bit Windows and 64bit Node.js. My "libdir" variable in this file reflects this location /bin/x64/vc12. If you are using x86, be sure to update this location.
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

Variable value: C:\opencv\build\x64\vc12

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

(--save-dev is optional, it assumes you want to save the installed version in the package.json file, though considering the
 --msvs_version flag, there might not be a point in saving it in your package.json file as npm install won't be useful without the flag)



7. Copy DLLs
---------------------------------------------

At this point, npm should have installed and compiled OpenCV for Node (with tons of warnings in your console I'm sure).

If so congrats!

Unfortunately, examples won't run due to missing DLLs. When running an example script you will get the following error:

module.js:356
  Module._extensions[extension](this, filename);
                               ^
Error: The specified module could not be found.

This is due to some linkage issues during the compilation process. The linkage is essentially non-existant, meaning the compiled
build/Release/opencv.node file will try to read the runtime DLLs adjacent to it. The final action you'll need to take is to copy
the contents of C:\opencv\build\x64\vc12\bin to <your-project>\node_modules\opencv\build\Release


NOW you should be good to go.


8. Final Step
-------------

Let's do some facial recognition on the Mona Lisa (as per the included examples)

Create a file in your folder root called "main.js"

Copy the following code into main.js:

var cv = require('opencv');
cv.readImage("mona.png", function(err, im){
  im.detectObject("haarcascade_frontalface_alt.xml", {}, function(err, faces){
        for (var i=0;i<faces.length; i++){
            var x = faces[i];
            im.ellipse(x.x + x.width/2, x.y + x.height/2, x.width/2, x.height/2);
        }
        im.save('out.png');
    });
});

Find "mona.png" and "haarcascade_frontalface_alt.xml" in the node-opencv example files and copy them to your project root.

Now in the command line, from the root of your project, issue the command "node main.js".

You should now have an "out.png" file at the root of your project with a circle around the Mona Lisa's face!

