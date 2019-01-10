cmake_minimum_required(VERSION 3.0)
project(statusengine-module)

set(CMAKE_INCLUDE_CURRENT_DIR ON)


include(FindPkgConfig)

find_package(PkgConfig REQUIRED)

pkg_check_modules(GEARMAND REQUIRED gearmand)
pkg_check_modules(JSONC REQUIRED json-c)
pkg_check_modules(GLIB REQUIRED glib-2.0)
add_library(statusengine SHARED statusengine.c )


target_include_directories(statusengine PUBLIC ${GEARMAND_INCLUDE_DIRS})
target_link_libraries(statusengine PUBLIC ${GEARMAND_LIBRARIES})
target_compile_options(statusengine PUBLIC ${GEARMAND_CFLAGS_OTHER})

add_definitions(-DWITH_RABBITMQ_CX080)


target_include_directories(statusengine PUBLIC ${JSONC_INCLUDE_DIRS})
target_link_libraries(statusengine PUBLIC ${JSONC_LIBRARIES})
target_compile_options(statusengine PUBLIC ${JSONC_CFLAGS_OTHER})

target_include_directories(statusengine PUBLIC ${GLIB_INCLUDE_DIRS})
target_link_libraries(statusengine PUBLIC ${GLIB_LIBRARIES})
target_compile_options(statusengine PUBLIC ${GLIB_CFLAGS_OTHER})

target_link_libraries(statusengine PUBLIC uuid event)


if(NAEMON)
    add_definitions(-DNAEMON)
endif(NAEMON)

if(NAGIOS)
    add_definitions(-DNAGIOS)
endif(NAGIOS)

if (NAEMON105)
    add_definitions(-DNAEMON105)
endif (NAEMON105)

install(TARGETS statusengine LIBRARY DESTINATION lib)