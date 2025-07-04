cmake_minimum_required(VERSION 3.14.4)
project(test_interface)

if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

# Set policy for 3.16 for CMP0076 defaulting to ON
cmake_policy(VERSION 3.16)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(quadrotor_msgs REQUIRED)

add_library(${PROJECT_NAME} INTERFACE
)

target_include_directories(${PROJECT_NAME}
  PUBLIC 
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>"
    "$<INSTALL_INTERFACE:include/${PROJECT_NAME}>"
)

target_link_libraries(${PROJECT_NAME} INTERFACE
  ${std_msgs_TARGETS}
)

add_executable(test_interface_node
  src/test_interface_node.cpp
)
target_link_libraries(test_interface_node PUBLIC
  ${PROJECT_NAME}
)

include(GNUInstallDirs)
install(
  TARGETS
    test_interface_node
  EXPORT export_${PROJECT_NAME}
  DESTINATION lib/${PROJECT_NAME}
)

install(DIRECTORY
  launch
  DESTINATION share/${PROJECT_NAME}/
)

ament_package()
