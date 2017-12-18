cmake_minimum_required(VERSION 2.8.3)

project(selective_search_3d)

find_package(catkin REQUIRED COMPONENTS
  message_generation
  roscpp
  sensor_msgs
  geometry_msgs
  std_msgs
  pcl_ros
  pcl_conversions
  image_geometry
  cv_bridge
)

find_package(PCL REQUIRED)

catkin_package(
  INCLUDE_DIRS include
  CATKIN_DEPENDS
  pcl_ros
  roscpp
  rospy
  
  DEPENDS PCL
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
  ${PCL_INCLUDE_DIRS}
)

add_executable(selective_search_3d
  src/selective_search_3d.cpp)
target_link_libraries(selective_search_3d
  ${catkin_LIBRARIES}
  ${PCL_LIBRARIES})

add_executable(selective_search_3d_offline
  src/selective_search_3d_offline.cpp)
target_link_libraries(selective_search_3d_offline
  ${catkin_LIBRARIES}
  ${PCL_LIBRARIES})

add_executable(show_bbox
  src/show_bbox.cpp)
target_link_libraries(show_bbox
  ${catkin_LIBRARIES}
  ${PCL_LIBRARIES})

add_executable(print_bbox3D
  src/print_bbox3D.cpp)
target_link_libraries(print_bbox3D
  ${catkin_LIBRARIES}
  ${PCL_LIBRARIES})

# rosbuild_add_executable(selective_search_3d src/selective_search_3d.cpp)
# rosbuild_add_executable(selective_search_3d_offline src/selective_search_3d_offline.cpp)
# rosbuild_add_executable(show_bbox src/show_bbox.cpp)
# rosbuild_add_executable(print_bbox3D src/print_bbox3D.cpp)
