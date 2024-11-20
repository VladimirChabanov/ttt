cmake_minimum_required(VERSION 3.10)

project(my-print)

# Add your library
add_library(my_print)

# Add include directories
target_include_directories(my_print INTERFACE 
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>   # for headers when building
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>  # for client in install mode
)

install(FILES print.h DESTINATION include)
# Generate the config file in the current binary dir (this ensures it's not placed directly in source)
file(WRITE "${CMAKE_CURRENT_BINARY_DIR}/my_print-config.cmake"
""
)
# Install the generated config file
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/my_print-config.cmake"
        DESTINATION share/my_print)
