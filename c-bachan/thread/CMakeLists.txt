cmake_minimum_required(VERSION 3.0)
project(thread LANGUAGES C)

add_executable(${PROJECT_NAME} "thread.c")
target_link_libraries(${PROJECT_NAME} PRIVATE Libev Threads::Threads header)
