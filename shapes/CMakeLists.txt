project(cpack-examples C)
cmake_minimum_required(VERSION 3.9)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "bin")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "lib")

find_package(Circle "1.0" REQUIRED CONFIG
  PATHS
    ${CMAKE_SOURCE_DIR}/../libraries/circle/build/install
)


add_executable(export-example
  ${CMAKE_CURRENT_LIST_DIR}/main.c
)
target_link_libraries(export-example
  PRIVATE
    Circle::circle
)

install(
  TARGETS export-example
  RUNTIME DESTINATION bin
)