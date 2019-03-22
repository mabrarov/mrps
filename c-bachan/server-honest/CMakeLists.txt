cmake_minimum_required(VERSION 3.0)
project(server-honest LANGUAGES C)

add_executable(${PROJECT_NAME} "server-honest.c")
target_link_libraries(${PROJECT_NAME} PRIVATE ev Threads::Threads header)