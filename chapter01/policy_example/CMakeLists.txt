# CMakeLists file for the Chapter 1 example illustrating how to set a policy
#
# SPDX-License-Identifier: MIT

cmake_minimum_required(VERSION 3.21)

project(
        ch1_policy_example
        VERSION 1.0
        DESCRIPTION
        "A simple C++ project to demonstrate creating a standalone executables"
        LANGUAGES CXX
)

# set policy CMP0121 to the old behavior. CMP0121 is a policy that detects if
# index variables for the list() commands are in a valid format this policy was
# introduced with cmake varsion 3.21
# 策略用于保持跨多个 CMake 版本的向后兼容性
cmake_policy(SET CMP0121 OLD) # CMP0121 策略设置为向后兼容的值, 用于检测 list() 的索引变量是否为有效格式--是否为整数

# Create a sample list
list(APPEND MYLIST "abc;def;ghi")
# This command will fail if the policy is set to NEW or if the call to
# cmake_policy above is removed as CMake 3.21 sets this policy automatically
list(GET MYLIST "any" OUT_VAR)