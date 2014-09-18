
PROJECT(fparser CXX)

cmake_minimum_required(VERSION 2.8)

#set(HEADERS fparser.hh fpconfig.hh fptypes.hh)
set(SOURCES fparser.cc fpoptimizer.cc)

ADD_LIBRARY(fparser SHARED ${SOURCES})

INSTALL(TARGETS fparser DESTINATION lib)

INSTALL(FILES fparser.hh DESTINATION include)

