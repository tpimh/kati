cmake_minimum_required(VERSION 3.1)
project(kati CXX)
set(CMAKE_CXX_STANDARD 11)
find_package(Threads)

include_directories(kati)
file(GLOB SOURCES src/*.cc)

add_executable(kati ${SOURCES})
set_target_properties(kati PROPERTIES LINKER_LANGUAGE CXX)
target_link_libraries(kati ${CMAKE_THREAD_LIBS_INIT})
