# 98 C++98
# 11 C++11
# 14 C++14
# 17 New in version 3.8. C++17
# 20 New in version 3.12. C++20
# 23 New in version 3.20. C++23
# 26 New in version 3.25. C++26

cmake_minimum_required(VERSION 3.20)
set (CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED On)
set(CMAKE_CXX_EXTENSIONS Off)

project(
  hands-on-design-patterns
  LANGUAGES C CXX)

enable_testing()

add_subdirectory(Chapter04)
