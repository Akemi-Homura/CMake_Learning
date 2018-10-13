cmake_minimum_required(VERSION 2.8)
project(foo NONE)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake/modules")

include(foo_run)

foo_run("123")

add_subdirectory(foo)
