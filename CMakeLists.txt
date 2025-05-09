cmake_minimum_required(VERSION 3.10)
project(vim-clangd LANGUAGES C CXX VERSION 0.0.1)

option(ENABLE_TESTS "Enable unit test" OFF)

# set default build type if not specified by user
if(NOT CMAKE_BUILD_TYPE)
	set(CMAKE_BUILD_TYPE "Release" CACHE STRING "Build type" FORCE)
endif()

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
	add_compile_options(-O0 -g)
	set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
else()
    add_compile_options(-O3 -Wall -Wextra)
endif()

set(CMAKE_C_STANDARD				11)
set(CMAKE_C_STANDARD_REQUIRED		ON)
set(CMAKE_CXX_STANDARD				11)
set(CMAKE_CXX_STANDARD_REQUIRED		ON)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY	${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY	${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY	${CMAKE_BINARY_DIR}/bin)

add_subdirectory(${CMAKE_SOURCE_DIR}/src)
add_subdirectory(${CMAKE_SOURCE_DIR}/3rd-party)

if(ENABLE_TESTS)
	enable_testing()
	add_subdirectory(${CMAKE_SOURCE_DIR}/test)
endif()

