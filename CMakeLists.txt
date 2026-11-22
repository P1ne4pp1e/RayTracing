cmake_minimum_required(VERSION 3.15)

project(WeekendRay LANGUAGES CXX)

add_executable(WeekendRay src/main.cc)
target_include_directories(WeekendRay PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}/src")

set_target_properties(WeekendRay PROPERTIES
    CXX_STANDARD 11
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO
)
