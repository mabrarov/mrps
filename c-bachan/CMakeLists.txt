cmake_minimum_required(VERSION 3.0)
project(c-bachan LANGUAGES C)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

find_package(Threads REQUIRED)
find_package(Libev REQUIRED)

add_subdirectory(header)
add_subdirectory(client)
add_subdirectory(server)
add_subdirectory(server-honest)
add_subdirectory(thread)
add_subdirectory(thread-honest)