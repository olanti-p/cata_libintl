cmake_minimum_required(VERSION 3.11)

project(cata_libintl LANGUAGES CXX)

option(CATA_LIBINTL_TESTS "Build tests" ON)

include(FetchContent)

add_subdirectory(src)

if(CMAKE_PROJECT_NAME STREQUAL PROJECT_NAME)
  include(CTest)
endif()

if(CATA_LIBINTL_TESTS)
  add_subdirectory(tests)
endif()
