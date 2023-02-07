set(SOURCES
  source.cc
)

add_library(archive STATIC ${SOURCES})
target_include_directories(archive PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

set(LIB_SOURCES
  lib.cc
)

set(PUBLIC_HEADERS
  include/header.h
)

add_library(mylib "${LIBRARY_TYPE}" ${LIB_SOURCES})
target_include_directories(mylib PUBLIC include)
target_link_libraries(mylib archive)

install(TARGETS mylib)
install(FILES ${PUBLIC_HEADERS} DESTINATION include)

set(BIN_SOURCES
  main.cc
)

add_executable(main ${BIN_SOURCES})
target_include_directories(main PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})
target_link_libraries(main mylib)

install(TARGETS main)
