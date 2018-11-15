project(triangle C)
cmake_minimum_required(VERSION 3.9)

add_library(triangle SHARED
  ${CMAKE_CURRENT_LIST_DIR}/triangle.c
)
target_include_directories(triangle
  PUBLIC
    ${CMAKE_CURRENT_LIST_DIR}/include
)

install(
  TARGETS
    triangle
  LIBRARY
    DESTINATION lib
)

install(
  DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/include/triangle
  DESTINATION include
  FILES_MATCHING PATTERN "*.h"
)