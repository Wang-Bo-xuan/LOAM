cmake_minimum_required(VERSION 2.4.6)
project(loam_continuous)

find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  nav_msgs
  sensor_msgs
  roscpp
  rospy
  std_msgs
  tf)

find_package(PCL REQUIRED)
find_package(OpenCV REQUIRED)

include_directories(
  include
	${catkin_INCLUDE_DIRS} 
	${PCL_INCLUDE_DIRS})

catkin_package(
  CATKIN_DEPENDS geometry_msgs nav_msgs roscpp rospy std_msgs pcl_conversions
  DEPENDS EIGEN3 PCL OpenCV
)


add_executable(continuous_scanRegistration src/scanRegistration.cpp)
target_link_libraries(continuous_scanRegistration ${catkin_LIBRARIES} ${PCL_LIBRARIES} ${OpenCV_LIBS})

add_executable(continuous_laserOdometry src/laserOdometry.cpp)
target_link_libraries(continuous_laserOdometry ${catkin_LIBRARIES} ${PCL_LIBRARIES} ${OpenCV_LIBS})

add_executable(continuous_laserMapping src/laserMapping.cpp)
target_link_libraries(continuous_laserMapping ${catkin_LIBRARIES} ${PCL_LIBRARIES} ${OpenCV_LIBS})

add_executable(continuous_transformMaintenance src/transformMaintenance.cpp)
target_link_libraries(continuous_transformMaintenance ${catkin_LIBRARIES} ${PCL_LIBRARIES} ${OpenCV_LIBS})
