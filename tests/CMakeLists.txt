cmake_minimum_required(VERSION 3.11)

FetchContent_Declare(
  catch
  GIT_REPOSITORY https://github.com/catchorg/Catch2.git
  GIT_TAG v2.13.8)

FetchContent_GetProperties(catch)
if(NOT catch_POPULATED)
  FetchContent_Populate(catch)
  add_subdirectory(${catch_SOURCE_DIR} ${catch_BINARY_DIR})
endif()

add_executable(cata_libintl_test cata_libintl_test.cpp)

target_link_libraries(cata_libintl_test PRIVATE cata_libintl Catch2)

add_test(
  NAME run_cata_libintl_test
  COMMAND cata_libintl_test
  WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})
