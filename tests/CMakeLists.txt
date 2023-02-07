set(TEST_SOURCES
  test-source.cc
)

add_executable(unittest EXCLUDE_FROM_ALL ${TEST_SOURCES})
target_link_libraries(unittest archive GTest::gtest_main)
