if(POLICY CMP0048)
  cmake_policy(SET CMP0048 NEW)
endif()

project(Circle VERSION 1.0.0 LANGUAGES C)
cmake_minimum_required(VERSION 3.9)


include(CMakePackageConfigHelpers)

write_basic_package_version_file(
  "CircleConfigVersion.cmake"
  VERSION ${Circle_VERSION}
  COMPATIBILITY SameMajorVersion
)

add_library(circle SHARED
  ${CMAKE_CURRENT_LIST_DIR}/circle.c
)
target_include_directories(circle
  PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/include>
    $<INSTALL_INTERFACE:include>
)

install(
  FILES "CircleConfig.cmake" "${CMAKE_CURRENT_BINARY_DIR}/CircleConfigVersion.cmake"
  DESTINATION lib/cmake/Circle
)

install(
  TARGETS circle
  EXPORT CircleTargets
  LIBRARY DESTINATION lib
  INCLUDES DESTINATION include
)

install(
  DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/include/circle
  EXPORT CircleTargets
  DESTINATION include
  FILES_MATCHING PATTERN "*.h"
)

install(
  EXPORT CircleTargets
  NAMESPACE Circle::
  DESTINATION lib/cmake/Circle
  FILE CircleTargets.cmake
)