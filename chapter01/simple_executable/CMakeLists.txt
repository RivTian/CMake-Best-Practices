# CMakeLists file for the Chapter 1 example illustrating how to create a simple executable
#
# SPDX-License-Identifier: MIT

cmake_minimum_required(VERSION 3.21)

# Define a CMake project
project(
        ch1_simple_executable
        VERSION 1.0
        DESCRIPTION "A simple C++ project to demonstrate basic CMake usage"
        LANGUAGES CXX)

# Add an executable target named `chapter1`
# 告诉 CMake 要构建一个可执行文件 (与库或自定义目标不同)。
add_executable(chapter1)
# Add sources to the target `chapter1`
# 告诉 CMake 在哪里查找名为 Chapter1 的可执行文件的源文件，并且源文件的可见性仅限于可执行文件。
target_sources(chapter1 PRIVATE src/main.cpp)