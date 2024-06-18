cmake_minimum_required(VERSION 3.12)

# Pull in SDK (must be before project)
include(pico_sdk_import.cmake)

project(pico-ttx4 C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Initialize the SDK
pico_sdk_init()

add_executable(pico-ttx4
        src/dev_lowlevel.c
        )

target_link_libraries(pico-ttx4 PRIVATE pico_stdlib hardware_resets hardware_irq)
pico_add_extra_outputs(pico-ttx4)
