cmake_minimum_required(VERSION 3.0)
project(server LANGUAGES C)

add_executable(${PROJECT_NAME} "server.c")
target_link_libraries(${PROJECT_NAME} PRIVATE header ev)
