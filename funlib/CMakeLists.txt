cmake_minimum_required(VERSION 3.22)

project(funlib)

add_library(funlib ${PROJECT_SOURCE_DIR}/src/funlib.cpp)

target_include_directories(funlib PUBLIC ${PROJECT_SOURCE_DIR}/include/funlib)

include(GNUInstallDirs)

# message(STATUS ${CMAKE_INSTALL_PREFIX})

install(TARGETS funlib)

install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/funlib
        DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})