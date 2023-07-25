cmake_minimum_required(VERSION 3.14)

project(example)

add_subdirectory(".." "Snap7")

add_executable(apartner "apartner.cpp")
target_link_libraries(apartner PRIVATE Snap7::Snap7)

add_executable(client "client.cpp")
target_link_libraries(client PRIVATE Snap7::Snap7)

add_executable(ppartner "ppartner.cpp")
target_link_libraries(ppartner PRIVATE Snap7::Snap7)

add_executable(server_v10 "server_v10.cpp")
target_link_libraries(server_v10 PRIVATE Snap7::Snap7)

add_executable(server "server.cpp")
target_link_libraries(server PRIVATE Snap7::Snap7)

add_executable(srv_resourceless "srv_resourceless.cpp")
target_link_libraries(srv_resourceless PRIVATE Snap7::Snap7)
