cmake_minimum_required(VERSION 3.5)

file(GLOB_RECURSE APGLIB_H "ApgLib/*.h")
file(GLOB_RECURSE APGLIB_C "ApgLib/*.c")
add_library(apg ${APGLIB_H} ${APGLIB_C})
add_library(apg::apg ALIAS apg)
target_include_directories(apg PUBLIC ApgLib/)

file(GLOB_RECURSE APGUTILS_H "ApgUtilities/*.h")
file(GLOB_RECURSE APGUTILS_C "ApgUtilities/*.c")
add_library(apg_utils ${APGUTILS_H} ${APGUTILS_C})
add_library(apg::utils ALIAS apg_utils)
target_include_directories(apg_utils PUBLIC ApgUtilities/)
target_link_libraries(apg_utils PUBLIC apg::apg)

file(GLOB_RECURSE GENERATOR_H "Generator/*.h")
file(GLOB_RECURSE GENERATOR_C "Generator/*.c")
add_executable(apg_generator ${GENERATOR_H} ${GENERATOR_C})

target_include_directories(apg_generator PRIVATE Generator/)
target_link_libraries(apg_generator PRIVATE apg::apg apg::utils)

