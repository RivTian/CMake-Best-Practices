# Example code for CMake Best Practices - Chapter 2

本章的项目结构为一个框架，其中包含三个CMake目标和使用该框架的示例驱动程序应用程序。该项目遵循基于组件的设计原则。

* The code requires a compiler which understands C++11. The requirement is specified in top-level CMakeLists file via setting `CMAKE_CXX_STANDARD` and `CMAKE_CXX_STANDARD_REQUIRED` variables.

* project() directive in sub-directory CMakeLists are used to eliminate redundant target name specification for a component.

* install() directive in top-level CMakeLists file makes all targets installable.