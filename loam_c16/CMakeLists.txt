cmake_minimum_required(VERSION 2.8.3)
project(loam_c16)

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
  CATKIN_DEPENDS geometry_msgs nav_msgs roscpp rospy std_msgs
  DEPENDS EIGEN3 PCL OpenCV
  INCLUDE_DIRS include
)


add_executable(c16_scanRegistration src/scanRegistration.cpp)
target_link_libraries(c16_scanRegistration ${catkin_LIBRARIES} ${PCL_LIBRARIES} ${OpenCV_LIBS})

add_executable(c16_laserOdometry src/laserOdometry.cpp)
target_link_libraries(c16_laserOdometry ${catkin_LIBRARIES} ${PCL_LIBRARIES} ${OpenCV_LIBS})

add_executable(c16_laserMapping src/laserMapping.cpp)
target_link_libraries(c16_laserMapping ${catkin_LIBRARIES} ${PCL_LIBRARIES} ${OpenCV_LIBS})

add_executable(c16_transformMaintenance src/transformMaintenance.cpp)
target_link_libraries(c16_transformMaintenance ${catkin_LIBRARIES} ${PCL_LIBRARIES} ${OpenCV_LIBS})

