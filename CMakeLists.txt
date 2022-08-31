cmake_minimum_required(VERSION 3.5)

include(family_support.cmake)

# gets PROJECT name for the example (e.g. <BOARD>-<DIR_NAME>)

project(pico-ttx4 C CXX ASM)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Checks this example is valid for the family and initializes the project
family_initialize_project(pico-ttx4 ${CMAKE_CURRENT_LIST_DIR})

add_executable(pico-ttx4)

# Example source
target_sources(pico-ttx4 PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/src/main.c
        ${CMAKE_CURRENT_SOURCE_DIR}/src/usb_descriptors.c
        )

# Example include
target_include_directories(pico-ttx4 PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/src
        )

# Configure compilation flags and libraries for the example... see the corresponding function
# in hw/bsp/FAMILY/family.cmake for details.
family_configure_device_example(pico-ttx4)
