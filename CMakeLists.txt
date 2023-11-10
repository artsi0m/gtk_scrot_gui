cmake_minimum_required(VERSION 3.27)
project(gtk_scrot_gui C)

set( CMAKE_C_COMPILER "/usr/local/bin/clang-13")
set( CMAKE_EXPORT_COMPILE_COMMANDS 1)
# Use the package PkgConfig to detect GTK+ headers/library files
find_package(PkgConfig REQUIRED)
pkg_check_modules(GTK REQUIRED gtk+-3.0)


add_executable(main main.c)
target_link_libraries(main PRIVATE ${GTK_LIBRARIES})


# Add other flags to the compiler
target_compile_definitions(main PRIVATE ${GTK_CFLAGS_OTHER})


# Setup CMake to use GTK+, tell the compiler where to look for headers
# and to the linker where to look for libraries
target_include_directories(main PRIVATE ${GTK_INCLUDE_DIRS})
target_link_directories(main PRIVATE ${GTK_LIBRARY_DIRS})
