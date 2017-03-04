cmake_minimum_required(VERSION 3.7)

project(iwyutest)
set(CMAKE_EXPORT_COMPILE_COMMANDS TRUE)

include_directories(
    "."
    )

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_C_STANDARD 11)

add_executable(quiettest mainquiet.cpp)
add_executable(loudtest mainloud.cpp)

find_program(iwyu_path NAMES include-what-you-use iwyu)
if(iwyu_path)
    set_property(TARGET quiettest PROPERTY C_INCLUDE_WHAT_YOU_USE ${iwyu_path})
    set_property(TARGET quiettest PROPERTY CXX_INCLUDE_WHAT_YOU_USE ${iwyu_path})
    set_property(TARGET loudtest PROPERTY C_INCLUDE_WHAT_YOU_USE ${iwyu_path})
    set_property(TARGET loudtest PROPERTY CXX_INCLUDE_WHAT_YOU_USE ${iwyu_path})
endif()
