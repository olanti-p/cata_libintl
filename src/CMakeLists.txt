add_library(
    cata_libintl cata_libintl.h cata_libintl.cpp
)

target_include_directories(
    cata_libintl PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}
)
