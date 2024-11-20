cmake_minimum_required(VERSION 3.10)

project(my-print)

message("CMAKE_INSTALL_PREFIX: ${CMAKE_INSTALL_PREFIX}")
install(FILES print.h DESTINATION include)

message("CMAKE_CURRENT_BINARY_DIR: ${CMAKE_CURRENT_BINARY_DIR}")
# Generate the config file in the current binary dir (this ensures it's not placed directly in source)
file(WRITE "${CMAKE_CURRENT_BINARY_DIR}/my_print-config.cmake"
""
)
# Install the generated config file
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/my_print-config.cmake"
        DESTINATION share/my_print)
