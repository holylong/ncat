cmake_minimum_required(VERSION 3.10)

project(netcat)

# set(CMAKE_C_COMPILER "i686-pc-mingw32-gcc")
# set(CMAKE_CXX_COMPILER "i686-pc-mingw32-g++")

if(WIN32)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DWIN32 -D_CONSOLE -DTELNET -DGAPING_SECURITY_HOLE")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DWIN32 -D_CONSOLE -DTELNET -DGAPING_SECURITY_HOLE")
elseif(UNIX)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -Wextra -pedantic -std=c11")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -pedantic -std=c++11")
endif()

add_executable(netcat getopt.c doexec.c netcat.c getopt.h generic.h)

include_directories(${CMAKE_CURRENT_SOURCE_DIR})
