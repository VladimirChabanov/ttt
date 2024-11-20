cmake_minimum_required(VERSION 3.10)

project(my_print)

# Add your library
add_library(my-print)

# Add include directories
target_include_directories(my-print INTERFACE 
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>   # for headers when building
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>  # for client in install mode
)

install(FILES print.h DESTINATION include)
