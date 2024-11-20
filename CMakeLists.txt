cmake_minimum_required(VERSION 3.10)

project(my_print)

# Add your library
add_library(my-print)

# Add include directories
target_include_directories(my-print INTERFACE 
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>   # for headers when building
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>  # for client in install mode
)

# Install the library and its headers
install(TARGETS my-print
        EXPORT my-print_targets)

install(FILES print.h DESTINATION include)

# Generate and install *-targets.cmake 
install(EXPORT my-print_targets
        FILE my-print-targets.cmake
        NAMESPACE my-print::
        DESTINATION share/my-print)

# Generate the config file in the current binary dir (this ensures it's not placed directly in source)
file(WRITE "${CMAKE_CURRENT_BINARY_DIR}/my-print-config.cmake"
"include(\"\${CMAKE_CURRENT_LIST_DIR}/my-print-targets.cmake\")\n"
)

# Install the generated config file
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/my-print-config.cmake"
        DESTINATION share/my-print)
