include(FetchContent)

FetchContent_Declare(gtest
  GIT_REPOSITORY https://github.com/google/googletest.git
  GIT_TAG release-1.12.1
)

set(INSTALL_GTEST OFF)
FetchContent_MakeAvailable(gtest)

set_target_properties(gtest gtest_main gmock gmock_main PROPERTIES
  EXCLUDE_FROM_ALL TRUE
)
