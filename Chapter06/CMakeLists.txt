cmake_path(GET CMAKE_CURRENT_BINARY_DIR FILENAME curr_dir)

include(FetchContent)

set(BENCHMARK_ENABLE_GTEST_TESTS OFF)
set(BENCHMARK_ENABLE_TESTING OFF)
FetchLibrary(
  https://github.com/google/benchmark.git
  main
)

set(target "${curr_dir}.exe")
add_executable(
    "${target}"
    smartptr.C
    smartptr_extra.C
)

target_link_libraries(
    "${target}"
    benchmark::benchmark)
