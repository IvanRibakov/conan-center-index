cmake_minimum_required(VERSION 3.1)
project(test_package)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

find_package(LibCDS REQUIRED CONFIG)

add_executable(${PROJECT_NAME} test_package.cpp)
set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 11)
if(LIBCDS_SHARED)
  target_link_libraries(${PROJECT_NAME} LibCDS::cds)
else()
  target_link_libraries(${PROJECT_NAME} LibCDS::cds-s)
endif()
