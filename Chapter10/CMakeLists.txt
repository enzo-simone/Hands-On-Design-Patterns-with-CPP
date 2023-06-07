cmake_path(GET CMAKE_CURRENT_BINARY_DIR FILENAME curr_dir)

set(CMAKE_BUILD_TYPE "Release")
set(BENCHMARK_ENABLE_GTEST_TESTS OFF)
set(BENCHMARK_ENABLE_TESTING OFF)
FetchLibrary(
  https://github.com/google/benchmark.git
  main
)

file(GLOB files "*.C")
foreach(file ${files})
    cmake_path(GET file FILENAME file)
    set(target "${curr_dir}-${file}.exe")
    add_executable(
        "${target}"
        "${file}"
    )
    target_link_libraries(
        "${target}"
        benchmark::benchmark)
endforeach()