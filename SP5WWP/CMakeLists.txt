# Project setup
cmake_minimum_required(VERSION 3.7.2)

if(${CMAKE_VERSION} VERSION_LESS "3.12.0")
    project(M17_Implementations)
else()
    project(M17_Implementations C)
endif()

include(GNUInstallDirs)

set(prefix "${CMAKE_INSTALL_PREFIX}")
set(exec_prefix \${prefix})
set(includedir \${prefix}/${CMAKE_INSTALL_INCLUDEDIR})
set(libdir \${exec_prefix}/${CMAKE_INSTALL_LIBDIR})

install(FILES
    inc/m17.h
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)

add_subdirectory(m17-decoder)
add_subdirectory(m17-coder)
add_subdirectory(m17-packet)

message(STATUS "Using install prefix: ${CMAKE_INSTALL_PREFIX}")
