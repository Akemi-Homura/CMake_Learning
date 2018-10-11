cmake_minimum_required(VERSION 2.8)
project(foo NONE)

set(ENV{USERNAME} "quals")
message("Environment variable USERNAME: $ENV{USERNAME}")
