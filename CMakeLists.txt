# Project setup
cmake_minimum_required(VERSION 3.7.2)

if(${CMAKE_VERSION} VERSION_LESS "3.12.0")
    project(M17_Implementations)
else()
    project(M17_Implementations C)
endif()

if(CMAKE_BUILD_TYPE STREQUAL "Release" AND NOT MSVC)
    if (CMAKE_C_COMPILER_ID MATCHES "GNU")
        set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -s")
    elseif (CMAKE_C_COMPILER_ID MATCHES "Clang")
        set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Oz")
    endif ()
endif()

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake/Modules)

include(GNUInstallDirs)
include(FindMath)

set(prefix "${CMAKE_INSTALL_PREFIX}")
set(exec_prefix \${prefix})
set(includedir \${prefix}/${CMAKE_INSTALL_INCLUDEDIR})
set(libdir \${exec_prefix}/${CMAKE_INSTALL_LIBDIR})

option(LINK_STATIC "Link statilally" OFF)
if(LINK_STATIC)
    set(STATIC_LNK "-static")
    message(STATUS "ENABLED statilally link")
else(LINK_STATIC)
    set(STATIC_LNK "")
    message(STATUS "DISABLED statically link")
endif(LINK_STATIC)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_CURRENT_BINARY_DIR})

set(libm17_SRC_DIR ${CMAKE_SOURCE_DIR}/libm17)

# add library
add_subdirectory(libm17-cmake)

# add utilities
add_subdirectory(SP5WWP/m17-decoder)
add_subdirectory(SP5WWP/m17-coder)
add_subdirectory(SP5WWP/m17-packet)


install(FILES
    "${CMAKE_CURRENT_SOURCE_DIR}/libm17/m17.h"
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)

# add uninstall target
configure_file(
    ${PROJECT_SOURCE_DIR}/cmake/cmake_uninstall.cmake.in
    ${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake
@ONLY)

add_custom_target(uninstall
    ${CMAKE_COMMAND} -P ${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake
)

message(STATUS "Using install prefix: ${CMAKE_INSTALL_PREFIX}")
