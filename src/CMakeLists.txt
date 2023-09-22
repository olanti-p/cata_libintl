cmake_minimum_required(VERSION 3.11)

FetchContent_Declare(
  fmtlib
  GIT_REPOSITORY https://github.com/fmtlib/fmt.git
  GIT_TAG 10.1.1)

FetchContent_GetProperties(fmtlib)
if(NOT fmtlib_POPULATED)
  FetchContent_Populate(fmtlib)
  add_subdirectory(${fmtlib_SOURCE_DIR} ${fmtlib_BINARY_DIR})
endif()

add_library(cata_libintl cata_libintl.h cata_libintl.cpp)

target_link_libraries(cata_libintl PRIVATE fmt::fmt)

target_include_directories(cata_libintl PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
