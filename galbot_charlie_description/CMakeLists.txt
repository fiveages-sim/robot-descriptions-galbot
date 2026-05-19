cmake_minimum_required(VERSION 3.8)
project(galbot_charlie_description)

find_package(ament_cmake REQUIRED)

install(
        DIRECTORY meshs xacro config urdf
        DESTINATION share/${PROJECT_NAME}/
)

ament_package()
