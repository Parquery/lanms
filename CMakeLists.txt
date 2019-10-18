cmake_minimum_required(VERSION 2.8)
set(CMAKE_CXX_FLAGS "-fpermissive -std=c++0x")

project(lanms_adaptor)

include_directories(include)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR}/cmake/)

add_library(clipper SHARED include/clipper/clipper.cpp)

add_subdirectory(pybind11)
pybind11_add_module(lanms_adaptor adaptor.cpp)
target_link_libraries(lanms_adaptor clipper)
