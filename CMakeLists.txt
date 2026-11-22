cmake_minimum_required(VERSION 3.15)

project(RayTracing LANGUAGES CXX)

add_executable(RayTracing src/main.cc)
target_include_directories(RayTracing PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}/src")

set_target_properties(RayTracing PROPERTIES
    CXX_STANDARD 11
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO
)
