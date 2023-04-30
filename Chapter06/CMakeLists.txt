cmake_path(GET CMAKE_CURRENT_BINARY_DIR FILENAME curr_dir)

include(FetchContent)

# ### Google Benchmark
set(BENCHMARK_ENABLE_GTEST_TESTS OFF)
set(BENCHMARK_ENABLE_TESTING OFF)
FetchContent_Declare(
    googlebenchmark
    GIT_REPOSITORY https://github.com/google/benchmark.git
    GIT_TAG main)

FetchContent_MakeAvailable(googlebenchmark)

# ###############
set(target "${curr_dir}.exe")
add_executable(
    "${target}"
    smartptr.C
    smartptr_extra.C
)

target_link_libraries(
    "${target}"
    benchmark::benchmark)
