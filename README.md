# Installing OpenCV with the extra modules

If all you need is the release version of OpenCV, you can install it via Homebrew. It comes by default with the extra and Non-free modules. CMake and pkg-config are useful to have either way.

1. Install homebrew from https://brew.sh
2. Install Xcode from the app store, or the developer tools via the command line: `xcode-select --install`
3. Accept the Xcode license agreement: `sudo xcodebuild -license accept`
4. Install cmake, pkg-config, and opencv from brew using `brew install cmake pkg-config opencv`

Then, all you need to do is follow the OpenCV include instructions for your favourite IDE. I have included instructions for using CMake, Eclipse, and XCode.

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


# Using OpenCV & Eclipse (Configuration Required)

[Click here for Eclipse Instructions](../blob/master/ECLIPSE.md)

# Using OpenCV & Xcode (Configuration Required)

[Click here for XCode Instructions](../blob/master/XCode.md)
