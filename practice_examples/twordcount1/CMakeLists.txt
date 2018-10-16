cmake_minimum_required(VERSION 2.8)
project(foo)

add_executable(twordcount1 twordcount1.cc)

add_definitions(-Wall)

foreach(lang C CXX)
    set(CMAKE_${lang}_FLAGS_DEBUG "-g3")
endforeach()

target_link_libraries(twordcount1 pthread)
