cmake_minimum_required(VERSION 3.12)
project(asio_benchmarks)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_BUILD_TYPE DEBUG)

include_directories(deps/boost/include)

link_directories(deps/boost/lib)

IF (APPLE)
    set(THREAD_LIB "boost_thread-mt")
ELSEIF (UNIX)
    set(THREAD_LIB "boost_thread -pthread")
ELSE()
    set(THREAD_LIB "boost_thread -pthread")
ENDIF ()


add_definitions(
        -DBOOST_ASIO_SEPARATE_COMPILATION
)

add_library(pre_asio src/libasio.cpp)

aux_source_directory(src/server2 SERVER2)
add_executable(server2 ${SERVER2})

aux_source_directory(src/server3 SERVER4)
add_executable(server3 ${SERVER4})
target_link_libraries(
        server2
        pre_asio
        ${THREAD_LIB}
)
target_link_libraries(
        server3
        pre_asio
        ${THREAD_LIB}
)
