cmake_minimum_required(VERSION 3.11)
project(ProjectName C CXX)

set(CMAKE_C_STANDARD 99)
set(CMAKE_CXX_STANDARD 17)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set(LIBRARY_TYPE "SHARED" CACHE STRING "Library type")
set(ENABLE_WERROR "ON" CACHE BOOL "Enable -Werror")
set(ADDRESS_SANITIZER "OFF" CACHE BOOL "Use address sanitizer")
set(EXTRA_FLAGS "" CACHE STRING "Additional compiler flags")

# Include these early so changes to compiler flags don't affect them
add_subdirectory(third-party)

add_compile_options(-Wall -Wextra -pedantic)

if(ENABLE_WERROR)
  add_compile_options(-Werror)
endif()

if(ADDRESS_SANITIZER)
  add_compile_options(-fsanitize=address)
endif()

add_compile_options(${EXTRA_FLAGS})

add_subdirectory(src)
add_subdirectory(tests)
