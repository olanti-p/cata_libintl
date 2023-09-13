cmake_minimum_required(VERSION 3.11)

project(
    cata_libintl
    LANGUAGES CXX
)

option(CATA_LIBINTL_TESTS   "Build tests"  ON)

add_subdirectory(src)
