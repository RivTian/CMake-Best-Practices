# CMakeLists creating a simple executable
#
# SPDX-License-Identifier: MIT

cmake_minimum_required(VERSION 3.21)

project(
        ch3_hello_world_standalone
        VERSION 1.0
        DESCRIPTION
        "A simple C++ project to demonstrate creating a standalone executables"
        LANGUAGES CXX
)

# 经常看到的一种常见模式是用项目名称来命名项目的可执行文件
# 乍一看这似乎很方便，但不推荐这样做。项目名称和目标具有不同的语义含义，因此应该将其
# 独立对待，因此应该避免使用 PROJECT_NAME 作为目标的名称。

# Create a target to build an executable
add_executable(ch3_hello_world_standalone)
# Add source files to 'hello_world' target
target_sources(ch3_hello_world_standalone PRIVATE src/main.cpp)
