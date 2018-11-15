project(pentagon C)
cmake_minimum_required(VERSION 3.9)

add_library(pentagon SHARED
  ${CMAKE_CURRENT_LIST_DIR}/pentagon.c
)
target_include_directories(pentagon
  PUBLIC
    ${CMAKE_CURRENT_LIST_DIR}/include
)

install(
  TARGETS
    pentagon
  LIBRARY
    DESTINATION lib
)

install(
  DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/include/pentagon
  DESTINATION include
  FILES_MATCHING PATTERN "*.h"
)