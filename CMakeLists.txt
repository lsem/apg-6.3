cmake_minimum_required(VERSION 3.5)

file(GLOB_RECURSE H_FILES1 "ApgLib/*.h")
file(GLOB_RECURSE C_FILES1 "ApgLib/*.c")
file(GLOB_RECURSE H_FILES2 "ApgUtilities/*.h")
file(GLOB_RECURSE C_FILES2 "ApgUtilities/*.c")

add_library(apg ${H_FILES1} ${C_FILES1} ${H_FILES2} ${C_FILES2})
add_library(apg::apg ALIAS apg)

target_include_directories(apg PUBLIC ApgLib/)
