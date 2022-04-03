cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

include($ENV{PICO_SDK_PATH}/external/pico_sdk_import.cmake)

project(test C CXX ASM)

pico_sdk_init()

add_subdirectory(sd-lib)
add_subdirectory(stdinit-lib)

add_executable(test main.c)

target_link_libraries(test PUBLIC pico_stdlib sd-lib stdinit-lib)

pico_enable_stdio_uart(test 1)
pico_enable_stdio_usb(test 0)

pico_add_extra_outputs(test)

