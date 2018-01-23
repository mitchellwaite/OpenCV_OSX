# Installing OpenCV with the extra modules

If all you need is the release version of OpenCV, you can install it via Homebrew. It comes by default with the extra and Non-free modules. CMake and pkg-config are useful to have either way.

1. Install homebrew from https://brew.sh
2. Install Xcode from the app store, or the developer tools via the command line: `xcode-select --install`
3. Accept the Xcode license agreement: `sudo xcodebuild -license accept`
4. Install cmake, pkg-config, and opencv from brew using `brew install cmake pkg-config opencv`

Then, all you need to do is follow the OpenCV include instructions for your favourite IDE. Or, skip to the instructions for `Using OpenCV & CMake` or `Using OpenCV & Eclipse` below.

# Installing the Debug version of OpenCV (Optional)

If you need to modify OpenCV for whatever reason, or would like extra debugging symbols, follow these instructions.

1. Install the Release version of OpenCV from the instructions above.

2. Download the opencv source, and the corresponding version of the opencv_contrib source zip release from the OpenCV git release

https://github.com/opencv/opencv/archive/3.4.0.zip

https://github.com/opencv/opencv_contrib/archive/3.4.0.zip

3. Extract both zip files to their individual directories
4. Change to the regular opencv directory
5. Make a `build` directory using `mkdir build-debug`
6. Change to the build-debug directory, and run the following command to prepare the OpenCV build. Change the extra modules path to the appropriate `modules` directory from the opencv_contrib directory

   `cmake -DCMAKE_INSTALL_PREFIX=/usr/local/opencv_debug -DCMAKE_BUILD_TYPE=Debug -DOPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-3.4.0/modules -DOPENCV_ENABLE_NONFREE=true ..`

7. Run `make -j4`, where 4 is the number of logical cores in your machine.
8. Once completed, if successful, run `make install`

If you wish to uninstall this version of OpenCV, you can run `make uninstall`, or `rm -rf /usr/local/opencv_debug`

# Using OpenCV & CMake (Easy)

1. Make a copy of this repository
2. Add your code to `lab.cpp`
3. Run `cmake .` to prepare the directory
4. Run `make` to build the executable. It will be called `lab`

# Using OpenCV & CMake (Custom, but easy)

1. Create a directory to contain your code.
2. Create a file called CMakeLists.txt, and copy the lines below in to it.

```
cmake_minimum_required(VERSION 2.8)
project( imshow )
find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_INCLUDE_DIRS} )
add_executable( imshow imshow.cpp )
target_link_libraries( imshow ${OpenCV_LIBS} )
```

3. Replace `imshow` in `project( imshow )` with a name of your choice.
4. Replace the first `imshow` in  `add_executable( imshow imshow.cpp )` with a name of your choice. This will become the executable file.
5. Replace `imshow.cpp` with the name of your source file(s)
6. Run `cmake .` to prepare the make file. If you add or remove source files, re-run this command.
7. Run `make` to build your project.


# Using OpenCV & Eclipse (Easy-ish)

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
