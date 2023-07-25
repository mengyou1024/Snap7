cmake_minimum_required(VERSION 3.14)

project(server)

add_subdirectory(".." "Snap7")

add_executable(${PROJECT_NAME} "server.cpp")
target_link_libraries(${PROJECT_NAME} PRIVATE Snap7::Snap7)
