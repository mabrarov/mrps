cmake_minimum_required(VERSION 3.0)
project(header LANGUAGES C)

add_library(${PROJECT_NAME} OBJECT "header.h")
target_include_directories(${PROJECT_NAME} INTERFACE ${PROJECT_SOURCE_DIR})