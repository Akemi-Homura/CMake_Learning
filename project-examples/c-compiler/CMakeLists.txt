cmake_minimum_required(VERSION 2.8)

message("Before 'project'")
message("  C: '${CMAKE_C_COMPILER}'")
message("  C++: '${CMAKE_CXX_COMPILER}''")

project(Foo C)

message("After 'project'")
message("  C: '${CMAKE_C_COMPILER}'")
message("  C++: '${CMAKE_CXX_COMPILER}'")
