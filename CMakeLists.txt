cmake_minimum_required(VERSION 3.10)

project(Snap7)

add_library(${PROJECT_NAME} STATIC "src/snap7.cpp")
target_include_directories(${PROJECT_NAME} PUBLIC "include")

if (CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
    target_link_libraries(${PROJECT_NAME} "${CMAKE_CURRENT_SOURCE_DIR}/lib/snap7.dll")
    execute_process(
        COMMAND ${CMAKE_COMMAND} -E copy
        "${CMAKE_CURRENT_SOURCE_DIR}/lib/snap7.dll"
        "${CMAKE_BINARY_DIR}/snap7.dll"
    )
elseif(CMAKE_CXX_COMPILER_ID STREQUAL "MSVC")
    target_link_libraries(${PROJECT_NAME} INTERFACE "${CMAKE_CURRENT_SOURCE_DIR}/lib/snap7.lib")
    if (CMAKE_BUILD_TYPE STREQUAL "Release")
        execute_process(
            COMMAND ${CMAKE_COMMAND} -E copy
            "${CMAKE_CURRENT_SOURCE_DIR}/lib/snap7.dll"
            "${CMAKE_BINARY_DIR}/${CMAKE_BUILD_TYPE}/snap7.dll"
        )
    else(CMAKE_BUILD_TYPE STREQUAL "Release")
        execute_process(
            COMMAND ${CMAKE_COMMAND} -E copy
            "${CMAKE_CURRENT_SOURCE_DIR}/lib/snap7.dll"
            "${CMAKE_BINARY_DIR}/Debug/snap7.dll"
        )
    endif(CMAKE_BUILD_TYPE STREQUAL "Release")
endif()
add_library("${PROJECT_NAME}::${PROJECT_NAME}" ALIAS ${PROJECT_NAME})
