cmake_minimum_required(VERSION 3.0)
project(client LANGUAGES C)

add_executable(${PROJECT_NAME} "client.c")
target_link_libraries(${PROJECT_NAME} PRIVATE Libev header)
