cmake_minimum_required(VERSION 3.15)

set(CMAKE_MODULE_PATH "${CMAKE_MODULE_PATH}" "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

include(GetCMakeMM)
cmmm(VERSION "2.0" REPOSITORY "flagarde/CMakeMM" PROVIDER "gitlab" VERBOSITY VERBOSE)

cmmm_modules_list(REPOSITORY "flagarde/CMakeCM" PROVIDER "gitlab")

project(SystemDetect VERSION 1.0 DESCRIPTION "Modern way to detect OS... with C++ and CMake" LANGUAGES C CXX)

option(BUILD_TESTS "Build the tests." ON)
option(BUILD_DOCS "Build the docs." ON)
option(BUILD_EXAMPLES "Build the examples." ON)

include(detect-arch)
include(detect-endianness)
include(detect-compiler)

if(BUILD_TESTS)
  include(CTest)
  add_subdirectory(tests)
endif()

if(BUILD_EXAMPLES)
  add_subdirectory(examples)
endif()

if(BUILD_DOCS)
  include(Documentations)
  add_subdirectory(docs)
endif()
