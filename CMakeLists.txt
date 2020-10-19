cmake_minimum_required(VERSION 3.12)
project(cpp_benchmarks)

#if (${PROJECT_BINARY_DIR} STREQUAL ${PROJECT_SOURCE_DIR})
#    message(FATAL_ERROR)
#endif()

set(CMAKE_CXX_STANDARD 14)

include(${PROJECT_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

add_executable(bm_string src/bm_demo.cpp)
conan_target_link_libraries(bm_string)
