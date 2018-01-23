# Using OpenCV & CMake

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
