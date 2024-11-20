cmake_minimum_required(VERSION 3.10)

project(my-print)

install(FILES print.h DESTINATION include)
# Generate the config file in the current binary dir (this ensures it's not placed directly in source)
file(WRITE "${CMAKE_CURRENT_BINARY_DIR}/my_print-config.cmake"
""
)
# Install the generated config file
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/my_print-config.cmake"
        DESTINATION share/my_print)
