cmake_minimum_required(VERSION 3.1)
project(kati CXX)
set(CMAKE_CXX_STANDARD 11)
find_package(Threads)
include(CheckCXXCompilerFlag)

CHECK_CXX_COMPILER_FLAG("-march=native" COMPILER_OPT_ARCH_NATIVE_SUPPORTED)
if (COMPILER_OPT_ARCH_NATIVE_SUPPORTED AND NOT CMAKE_CXX_FLAGS MATCHES "-march=")
	SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -march=native")
endif()

add_definitions(-DNOLOG)

include_directories(kati)
file(GLOB SOURCES src/*.cc)

add_executable(kati ${SOURCES})
set_target_properties(kati PROPERTIES LINKER_LANGUAGE CXX)
target_link_libraries(kati ${CMAKE_THREAD_LIBS_INIT})
