cmake_minimum_required(VERSION 2.8)
project( lab )
find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_INCLUDE_DIRS} )
add_executable( lab lab.cpp )
target_link_libraries( lab ${OpenCV_LIBS} )

