cmake_minimum_required(VERSION 2.8)
project( imshow )
find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_INCLUDE_DIRS} )
add_executable( imshow imshow.cpp )
target_link_libraries( imshow ${OpenCV_LIBS} )

