# Installing OpenCV with the extra modules

1. Install homebrew from brew.sh
2. Install Xcode and the developer tools
3. Install cmake from brew using `brew install cmake`
4. Download the opencv source, and the corresponding version of the opencv_contrib source zip release from the OpenCV git release

https://github.com/opencv/opencv/archive/3.4.0.zip

https://github.com/opencv/opencv_contrib/archive/3.4.0.zip

5. Extract both zip files to their individual directories
6. Change to the regular opencv directory
7. Make a `build` directory using `mkdir build`
8. Change to the build directory, and run the following command to build OpenCV. Change the extra modules path to the appropriate `modules` directory from the opencv_contrib directory
   `cmake -DOPENCV_EXTRA_MODULES_PATH=../path/to/opencv_contrib-3.4.0/modules ..`
9. Run `make -j4`, where 4 is the number of logical cores in your machine.
10. Once completed, if successful, run `make install`

# Using OpenCV & CMake (Easy)

1. Make a copy of this repository
2. Add your code to `lab.cpp`
3. Run `cmake .` to prepare the directory
4. Run `make` to build the executable. It will be called `lab`

# Using OpenCV & CMake (Custom)

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
