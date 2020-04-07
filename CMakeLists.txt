cmake_minimum_required(VERSION 3.10 FATAL_ERROR)

project(matplotlibcpp DESCRIPTION "Possibly the simplest C++ plotting library")

add_library(matplotlibcpp INTERFACE)

find_package(Python2 COMPONENTS Development NumPy REQUIRED)

target_link_libraries(matplotlibcpp
    INTERFACE
        Python2::Python
        Python2::NumPy
)

target_include_directories(matplotlibcpp
    INTERFACE
        ${Python2_INCLUDE_DIRS}
        ${Python2_NumPy_INCLUDE_DIRS}
)

target_include_directories(matplotlibcpp INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
    $<INSTALL_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
)
