cmake_minimum_required(VERSION 3.0)

cmake_policy(SET CMP0048 NEW)
project(my_gtest_pkgconfig VERSION 0.0.1 LANGUAGES CXX)

find_package(PkgConfig)
pkg_search_module(GTEST REQUIRED gtest_main)

message("PKG_CONFIG_USE_CMAKE_PREFIX_PATH ${PKG_CONFIG_USE_CMAKE_PREFIX_PATH}")

foreach(x RANGE 1 10)
    if(x EQUAL 3)
        add_executable(sample3 sample3_unittest.cc)
        continue()
    endif()
    if(x LESS_EQUAL 4)
        add_executable(sample${x} sample${x}.cc sample${x}_unittest.cc)
    elseif(x EQUAL 5)
        add_executable(sample5 sample5_unittest.cc sample1.cc)
    else()
        add_executable(sample${x} sample${x}_unittest.cc)
    endif()
endforeach()

foreach(x RANGE 1 10)
    target_link_libraries(sample${x} ${GTEST_LDFLAGS})
    target_compile_options(sample${x} PUBLIC ${GTEST_CFLAGS})
endforeach()

include(CTest)
foreach(x RANGE 1 10)
    add_test(sample${x}_test sample${x})
endforeach()
