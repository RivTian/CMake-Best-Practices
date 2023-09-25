# CMakeLists file for the Chapter 4 Example nr. 01: 
# Installable executable
#
# SPDX-License-Identifier: MIT

cmake_minimum_required(VERSION 3.21)

project(
        ch4_ex01_executable
        VERSION 1.0
        DESCRIPTION "Chapter 4 Example 01, installable executable project"
        LANGUAGES CXX)

#  定义了一个可执行目标, 随后的两行中填充了它的属性

# Define an executable target named `ch4_ex01_executable`
add_executable(ch4_ex01_executable)
# Specify source files for target named `ch4_ex01_executable`
target_sources(ch4_ex01_executable PRIVATE src/main.cpp)
# Request compile features for target named `ch4_ex01_executable`.
# Requested `cxx_std_11` feature determines the minimum C++ standard required
# to build this target. It's PRIVATE, since it is a build-time requirement only.
target_compile_features(ch4_ex01_executable PRIVATE cxx_std_11)
# Make executable target `ch4_ex01_executable` installable. As mentioned before
# in Chapter 4 content, this will only install the output artifacts produced by the target.
install(TARGETS ch4_ex01_executable # )
        RUNTIME DESTINATION qbin
)

# 最后一行 install 则是我们所关心的 ch4-ex01-executable 所需的安装代码