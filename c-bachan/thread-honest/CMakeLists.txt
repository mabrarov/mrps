cmake_minimum_required(VERSION 3.0)
project(thread-honest LANGUAGES C)

add_executable(${PROJECT_NAME} "thread-honest.c")
target_link_libraries(${PROJECT_NAME} PRIVATE Libev Threads::Threads header)
