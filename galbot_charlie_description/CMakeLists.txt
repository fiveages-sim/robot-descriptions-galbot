cmake_minimum_required(VERSION 3.14)
project(galbot_charlie_description)

find_package(ament_cmake REQUIRED)

install(
        DIRECTORY meshs xacro config
        DESTINATION share/${PROJECT_NAME}/
)

ament_package()
