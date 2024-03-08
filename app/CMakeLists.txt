cmake_minimum_required(VERSION 3.22)

project(cpp-workshop)

add_executable(workshop src/main.cpp)

include(GNUInstallDirs)
target_link_libraries(workshop funlib)