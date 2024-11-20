cmake_minimum_required(VERSION 3.10)

project(my_print)

include(GNUInstallDirs)

install(FILES print.h DESTINATION include)

# Generate and install *-targets.cmake 
install(EXPORT my-print_targets
        FILE my-print-targets.cmake
        DESTINATION share/my-print)

# Generate the config file in the current binary dir (this ensures it's not placed directly in source)
file(WRITE "${CMAKE_CURRENT_BINARY_DIR}/my-print-config.cmake"
"include(CMakeFindDependencyMacro)\n"
"find_dependency(fmt CONFIG REQUIRED)\n"
"include(\"\${CMAKE_CURRENT_LIST_DIR}/my-print-targets.cmake\")\n"
)

# Install the generated config file
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/my-print-config.cmake"
        DESTINATION share/my-print)
