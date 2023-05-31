set(target function_call.exe)
add_executable("${target}" function_call.C)

set(BENCHMARK_ENABLE_GTEST_TESTS OFF)
set(BENCHMARK_ENABLE_TESTING OFF)
FetchLibrary(
    https://github.com/google/benchmark.git
    main
)
target_link_libraries("${target}" benchmark::benchmark)
