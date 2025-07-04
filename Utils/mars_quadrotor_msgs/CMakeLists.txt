cmake_minimum_required(VERSION 3.14.4)
project(quadrotor_msgs)

find_package(ament_cmake REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)

include_directories(
        ${catkin_INCLUDE_DIRS}
        include
)

rosidl_generate_interfaces(${PROJECT_NAME}
        msg/EsdfMap.msg
        msg/FcToOa.msg
        msg/Oaresult.msg
        msg/Vioresult.msg
        msg/Ctrl.msg
        msg/Aec.msg
        msg/AuxCommand.msg
        msg/Corrections.msg
        msg/Gains.msg
        msg/OutputData.msg
        msg/PositionCommand.msg
        msg/PPROutputData.msg
        msg/Serial.msg
        msg/SO3Command.msg
        msg/StatusData.msg
        msg/TRPYCommand.msg
        msg/Odometry.msg
        msg/PolynomialTrajectory.msg
        msg/MincoTrajectory.msg
        msg/LQRTrajectory.msg
        msg/Droneaecinfo.msg
        msg/Oamanagerdebug.msg
        msg/TakeoffLand.msg
        msg/Px4ctrlDebug.msg
        msg/ServerTime.msg
        msg/TrakingPerformance.msg
        msg/MpcPositionCommand.msg
        msg/QuadrotorState.msg
        DEPENDENCIES geometry_msgs nav_msgs
)

# catkin_package(
#         #INCLUDE_DIRS include
#         LIBRARIES encode_msgs decode_msgs
#         #CATKIN_DEPENDS geometry_msgs nav_msgs
#         #DEPENDS system_lib
#         CATKIN_DEPENDS message_runtime
# )

# # add_executable(test_exe src/test_exe.cpp)
# add_library(decode_msgs src/decode_msgs.cpp)
# add_library(encode_msgs src/encode_msgs.cpp)

# # add_dependencies(test_exe quadrotor_msgs_generate_messages_cpp)
# add_dependencies(encode_msgs quadrotor_msgs_generate_messages_cpp)
# add_dependencies(decode_msgs quadrotor_msgs_generate_messages_cpp)

# find_package(Eigen3 REQUIRED)
# include_directories(${EIGEN3_INCLUDE_DIR})


# target_link_libraries(test_exe 
#     decode_msgs 
#     encode_msgs
# )

ament_export_dependencies(rosidl_default_runtime)

ament_package()
