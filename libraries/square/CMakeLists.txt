project(square C)
cmake_minimum_required(VERSION 3.9)

add_library(square SHARED
  ${CMAKE_CURRENT_LIST_DIR}/square.c
)
target_include_directories(square
  PUBLIC
    ${CMAKE_CURRENT_LIST_DIR}/include
)

install(
  TARGETS
    square
  LIBRARY
    DESTINATION lib
)

install(
  DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/include/square
  DESTINATION include
  FILES_MATCHING PATTERN "*.h"
)