# OpenCV and Eclipse

1. Install the latest JDK for macOS: `https://docs.oracle.com/javase/8/docs/technotes/guides/install/mac_jdk.html`. Eclipse requires the full JDK on MacOS, the JRE from Oracle or Apple isn't enough.
2. Install an Eclipse for C/C++ developers package: `https://www.eclipse.org/downloads/packages/`. Make sure to get the latest version. At the time of writing this, it is `Oxygen 2 v`
3. Open Eclipse, and create a new C++ project. Select `C++ Managed Build`
4. Give your project a name. Under `Project Type` select `Executable` -> `Hello World C++ Project`
5. Under `Toolchains`, select `MacOS GCC`. Then press next.
6. Add an author, copyright notice, or hello world greeting if you wish, then press next again.
7. Click `Advanced Settings`

## Release only version of OpenCV

1. Under `Configurations` select `All Configurations`
2. Under `C/C++ Build` select `Settings`. Then under `MacOS X C++ Linker` select `Settings`.
3. Under `Libraries` click on the page with a plus icon. Paste the following text. This represents all OpenCV libraries installed by the Homebrew package. To list all libraries on system, use `pkg-config --libs opencv`Then use a text editor to remove '-l' and add ';' between each library.:

`opencv_stitching;opencv_superres;opencv_videostab;opencv_aruco;opencv_bgsegm;opencv_bioinspired;opencv_ccalib;opencv_dpm;opencv_face;opencv_photo;opencv_fuzzy;opencv_img_hash;opencv_line_descriptor;opencv_optflow;opencv_reg;opencv_rgbd;opencv_saliency;opencv_stereo;opencv_structured_light;opencv_phase_unwrapping;opencv_surface_matching;opencv_tracking;opencv_datasets;opencv_text;opencv_dnn;opencv_plot;opencv_xfeatures2d;opencv_shape;opencv_video;opencv_ml;opencv_ximgproc;opencv_calib3d;opencv_features2d;opencv_highgui;opencv_videoio;opencv_flann;opencv_xobjdetect;opencv_imgcodecs;opencv_objdetect;opencv_xphoto;opencv_imgproc;opencv_core`

4. Under `Libraries` click on the page with a plus icon. Paste the following text. This represents where the libraries are installed by the Homebrew package.

`/usr/local/lib`

5. Click `Apply and Close`, then `Finish`
6. You should now be able to build and run your project!

## Debug only version of OpenCV

You must follow the similar instructions for the release only version. In step 4, replace `/usr/local/lib` with the location of the OpenCV libraries.

## Both debug and release versions of OpenCV

You must complete the instructions twice.

1. Instead of selecting `All Configurations`, select `Release`
2. Complete the rest of the instructions.
3. When you reach Step 5, Click `Apply`. *DO NOT CLICK* `Apply and Close`
4. Under `Configurations`, select `Debug`
5. Complete step 3 as written.
6. In step 4, replace `/usr/local/lib` with the location of the OpenCV debug libraries.
7. Click `Apply and Close`, then `Finish`
8. You should now be able to build and run your project! `Release` mode will build and link against the regular OpenCV libraries, while `Debug` mode will link against the Debug OpenCV libraries
