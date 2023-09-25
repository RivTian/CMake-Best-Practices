# Top-level CMakeLists
# file for the CMake Best Practices book CMake example project
#
# SPDX-License-Identifier: MIT

#指定生成此项目所需的最低CMake版本（以及
#子项目）子项目可以通过指定另一个版本来覆盖此值
#其CMakeLists文件中的要求（例如，要求CMake的更高版本）
cmake_minimum_required(VERSION 3.21)

# The main project
project(
        "CMakeBestPractices"
        VERSION 1.0
        DESCRIPTION
        "The 'build-all' instructions for all examples for the book CMake Best Practices"
        LANGUAGES CXX
)
include(CTest)

#设置单个配置生成器的默认生成类型。生成类型
#变量仍然可以从外部重写。
set(CMAKE_BUILD_TYPE
        "Debug"
        CACHE STRING "Default build type for single-config generators"
)

set(CMAKE_EXPORT_COMPILE_COMMANDS TRUE)

#打印生成器类型和生成类型（如果适用）
get_property(
        is_multi_config_generator GLOBAL
        PROPERTY GENERATOR_IS_MULTI_CONFIG
)
if (NOT is_multi_config_generator)
    message(STATUS "Using a single-config generator (${CMAKE_GENERATOR})")
    message(STATUS "Current build type is `${CMAKE_BUILD_TYPE}`")
else ()
    message(STATUS "Using a multi-config generator (${CMAKE_GENERATOR})")
endif ()

find_program(CCACHE_PROGRAM ccache)
if (CCACHE_PROGRAM)
    set(CMAKE_C_COMPILER_LAUNCHER ${CCACHE_PROGRAM})
    set(CMAKE_CXX_COMPILER_LAUNCHER ${CCACHE_PROGRAM})
endif ()

# Add chapter examples to root project
add_subdirectory(chapter01)
add_subdirectory(chapter02)
add_subdirectory(chapter03)
add_subdirectory(chapter04)
#add_subdirectory(chapter05)
#add_subdirectory(chapter06)
#add_subdirectory(chapter07)
#add_subdirectory(chapter08)
# the chapter 10 examples are intended to be built standalone
# add_subdirectory(chapter10)
#add_subdirectory(chapter11)
#add_subdirectory(chapter12)
#add_subdirectory(chapter13)
#add_subdirectory(chapter14)