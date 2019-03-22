cmake_minimum_required(VERSION 3.0)
project(c-bachan LANGUAGES C)

find_package(Threads REQUIRED)

add_subdirectory(header)
add_subdirectory(client)
add_subdirectory(server)
add_subdirectory(server-honest)
add_subdirectory(thread)
add_subdirectory(thread-honest)