cmake_minimum_required(VERSION 3.0)

project(win2alt)

add_executable(win2alt win2alt.c)
target_compile_options(win2alt PRIVATE -Wall -Wextra)

install(TARGETS win2alt RUNTIME DESTINATION bin)
