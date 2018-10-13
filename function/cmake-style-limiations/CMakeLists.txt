cmake_minimum_required(VERSION 2.8)
project(foo NONE)

include(CMakeParseArguments)

function(foo)
    set(optional "")
    set(one X)
    set(multiple "")

    # Introduce
    # * x_X
    cmake_parse_arguments(x "${optional}" "${one}" "${multiple}" "${ARGV}")

    string(COMPARE NOTEQUAL "${x_UNPARSED_ARGUMENTS}" "" has_unparsed)
    if(has_unparsed)
        message(FATAL_ERROR "Unparsed arguments: ${x_UNPARSED_ARGUMENTS}")
    endif()

    if(DEFINED x_X)
        set(is_define YES)
    else()
        set(is_define NO)
    endif()

    message("X is defined: ${is_define}")
    message("X value: '${x_X}'")
endfunction()

message("*** Run (1) ***")
foo(X "")

message("*** Run (2) ***")
foo(X)

message("*** Run (3) ***")
foo()
