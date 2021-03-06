cmake_minimum_required(VERSION 2.8.3)
project(hrp2jsknt_moveit_demos)

find_package(catkin REQUIRED COMPONENTS
  ompl_thunder
  moveit_humanoid_stability
  moveit_core
  ompl_visual_tools
  moveit_planners_ompl
  random_numbers
  moveit_core 
  moveit_ros_planning 
  pluginlib
  moveit_visual_tools
  cmake_modules
)

find_package(Eigen REQUIRED)
find_package(Boost REQUIRED system filesystem date_time thread)

catkin_package(
#  INCLUDE_DIRS include
  CATKIN_DEPENDS
    ompl_thunder
    moveit_humanoid_stability
    moveit_core
    ompl_visual_tools
    moveit_planners_ompl
    random_numbers
    moveit_core
    moveit_ros_planning
    interactive_markers
    moveit_visual_tools
  DEPENDS
    Eigen
)

###########
## Build ##
###########
include_directories(SYSTEM 
  ${Boost_INCLUDE_DIR} 
  ${EIGEN_INCLUDE_DIRS})
include_directories(${catkin_INCLUDE_DIRS})
link_directories(${catkin_LIBRARY_DIRS})

add_executable(hrp2_demos src/hrp2_demos.cpp)
target_link_libraries(hrp2_demos ${catkin_LIBRARIES} ${Boost_LIBRARIES})