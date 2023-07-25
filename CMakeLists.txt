cmake_minimum_required(VERSION 3.10)

project(Snap7)

add_library(${PROJECT_NAME} STATIC "src/snap7.cpp")
target_link_libraries(${PROJECT_NAME} "${CMAKE_CURRENT_SOURCE_DIR}/lib/snap7.dll")
target_include_directories(${PROJECT_NAME} PUBLIC "include")
add_library("${PROJECT_NAME}::${PROJECT_NAME}" ALIAS ${PROJECT_NAME})

execute_process(
    COMMAND ${CMAKE_COMMAND} -E copy 
    "${CMAKE_CURRENT_LIST_DIR}/lib/snap7.dll"
    "${CMAKE_BINARY_DIR}/snap7.dll"
)

