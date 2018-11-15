project(hexagon C)
cmake_minimum_required(VERSION 3.9)

add_library(hexagon SHARED
  ${CMAKE_CURRENT_LIST_DIR}/hexagon.c
)
target_include_directories(hexagon
  PUBLIC
    ${CMAKE_CURRENT_LIST_DIR}/include
)

install(
  TARGETS hexagon
  EXPORT hexagon-config
  LIBRARY
    DESTINATION lib
)

install(
  DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/include/hexagon
  EXPORT hexagon-config
  DESTINATION include
  FILES_MATCHING PATTERN "*.h"
)

install(
  EXPORT hexagon-config
  NAMESPACE Hexagon::
  DESTINATION cmake
  FILE FindHexagon.cmake
)