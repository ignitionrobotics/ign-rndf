include_directories (
  ${PROJECT_SOURCE_DIR}/test/gtest/include
  ${PROJECT_SOURCE_DIR}/test/gtest
  ${PROJECT_SOURCE_DIR}/test
  ${PROJECT_BINARY_DIR}
)

# Build gtest
add_library(gtest STATIC gtest/src/gtest-all.cc)
add_library(gtest_main STATIC gtest/src/gtest_main.cc)
target_link_libraries(gtest_main gtest)
set(GTEST_LIBRARY "${PROJECT_BINARY_DIR}/test/libgtest.a")
set(GTEST_MAIN_LIBRARY "${PROJECT_BINARY_DIR}/test/libgtest_main.a")

add_subdirectory(integration)
add_subdirectory(performance)
add_subdirectory(regression)

configure_file (test_config.h.in ${PROJECT_BINARY_DIR}/include/ignition/rndf/test_config.h)
