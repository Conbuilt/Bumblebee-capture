cmake_minimum_required(VERSION 2.8.3)
project(xb3)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  sensor_msgs
  std_msgs
  cv_bridge
  image_transport
)
find_package(OpenCV REQUIRED)

catkin_package()

include_directories(
  ${catkin_INCLUDE_DIRS}
  ${OpenCV_LIBRARIES}
  /usr/include/triclops
  /usr/include/flycapture
)

add_executable(xb3_client src/xb3_client.cpp)
add_executable(triXB3 src/triXB3.cpp)

## Specify libraries to link a library or executable target against
target_link_libraries(xb3_client
  ${catkin_LIBRARIES}
  ${OpenCV_LIBRARIES}
)

target_link_libraries(triXB3
  ${catkin_LIBRARIES}
  ${OpenCV_LIBRARIES}
  triclops
  pnmutils
  flycapture
  flycapture2bridge
  pthread
)