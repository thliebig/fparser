
# define build type
SET( CMAKE_BUILD_TYPE Release )

PROJECT(fparser CXX)

# In CMake 4, 3.10 is deprecated and 3.5 has been removed.
# use 3.0...3.10 so all of these versions are acceptable as min. version.
# https://cmake.org/cmake/help/latest/command/cmake_minimum_required.html
cmake_minimum_required(VERSION 3.0...3.10)

# default
set(LIB_VERSION_MAJOR 4)
set(LIB_VERSION_MINOR 5)
set(LIB_VERSION_PATCH 1)
set(LIB_VERSION_STRING ${LIB_VERSION_MAJOR}.${LIB_VERSION_MINOR}.${LIB_VERSION_PATCH})

set(VERSION "v${LIB_VERSION_STRING}")

if(APPLE AND NOT CMAKE_INSTALL_NAME_DIR)
  set(CMAKE_INSTALL_NAME_DIR "${CMAKE_INSTALL_PREFIX}/lib${LIB_SUFFIX}")
endif()

#set(HEADERS fparser.hh fpconfig.hh fptypes.hh)
set(SOURCES fparser.cc fpoptimizer.cc)

remove(CMAKE_CXX_FLAGS -Dfparser_EXPORTS)

ADD_LIBRARY(fparser SHARED ${SOURCES})

set_target_properties(fparser PROPERTIES VERSION ${LIB_VERSION_STRING} SOVERSION ${LIB_VERSION_MAJOR})

INSTALL(TARGETS fparser DESTINATION lib${LIB_SUFFIX})

INSTALL(FILES fparser.hh DESTINATION include)

