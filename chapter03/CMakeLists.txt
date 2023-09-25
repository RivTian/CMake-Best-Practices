# Top-level CMakeLists file for the Chapter 3 example content.
#
# SPDX-License-Identifier: MIT

cmake_minimum_required(VERSION 3.21)

project(
        chapter_3
        VERSION 1.0
        DESCRIPTION
        "A collection of sample C++ applications and libraries to demonstrate creating libraries and executables"
        LANGUAGES CXX
)

# Add subdirectories with examples
add_subdirectory(hello_world_standalone)
add_subdirectory(hello_shared_lib)
add_subdirectory(hello_static_lib)
add_subdirectory(hello_header_only)
add_subdirectory(hello_object_lib)

# add an example executable
add_executable(chapter3)
# add sources to the example executable
target_sources(chapter3 PRIVATE src/main.cpp)
# link libraries "hello" and "hello_header_only" to the example executable the
# libraries are described in the subdirectories
# 使用静态库即可运行，shared 直接运行会提示缺失 dll 文件，需要手动在 build/hello_shared_lib 下 cv dll 文件到 exe 同级文件夹下
target_link_libraries(chapter3 PRIVATE ch3_hello_header_only ch3_hello_object ch3_hello_static) #ch3_hello_shared ch3_hello_object)

# Private 用于链接库，仅构建目标时才需要链接库
# Interface 没有链接到库，当在其他地方需要使用目标时，链接库是必须的，通常仅限于 头文件库 时使用
# Public 链接到库，该库既是构建依赖项，也是使用依赖项