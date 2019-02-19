cmake_minimum_required(VERSION 2.8.3)
project(sim_plugins)

add_definitions(-std=c++11)

# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED COMPONENTS
  roscpp
  gazebo_ros
)

# Depend on system install of Gazebo
find_package(gazebo REQUIRED)

link_directories(${GAZEBO_LIBRARY_DIRS})
include_directories(${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS} ${GAZEBO_INCLUDE_DIRS})

add_library(happy_world src/hello_world_plugin.cpp )
target_link_libraries(happy_world ${catkin_LIBRARIES} ${GAZEBO_LIBRARIES})

add_library(model_pusher src/model_push.cpp )
target_link_libraries(model_pusher ${catkin_LIBRARIES} ${GAZEBO_LIBRARIES})


catkin_package(
  DEPENDS
    roscpp
    gazebo_ros
)
