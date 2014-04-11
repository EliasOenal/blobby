cmake_minimum_required(VERSION 2.6)

include(CPack)

project(Blobby)

option(MAC_OS_X "Building OS X version" OFF)
if (MAC_OS_X)
    add_definitions(-D MAC_OS_X)
    INCLUDE_DIRECTORIES(/opt/local/include)
    LINK_DIRECTORIES(/opt/local/lib)
endif (MAC_OS_X)

# process the config.h
configure_file(${Blobby_SOURCE_DIR}/config.h.in
               ${Blobby_BINARY_DIR}/config.h)
include_directories(${Blobby_BINARY_DIR})

add_subdirectory(data)
add_subdirectory(src)

