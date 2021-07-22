cmake_minimum_required(VERSION 3.15)

project(SystemDetect VERSION 1.0 LANGUAGES C CXX)

option(BUILD_TESTS "Build the tests." ON)
option(BUILD_EXAMPLES "Build the examples." ON)

if(BUILD_TESTS)
  include(CTest)
  add_subdirectory(tests)
endif()

if(BUILD_EXAMPLES)
  add_subdirectory(examples)
endif()
