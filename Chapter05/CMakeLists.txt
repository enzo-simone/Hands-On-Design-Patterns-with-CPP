cmake_path(GET CMAKE_CURRENT_BINARY_DIR FILENAME curr_dir)
include(FetchContent)

# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchLibrary(
  https://github.com/google/googletest.git
  main)

include(GoogleTest)

foreach(file memory1.C mutex1.C scoped_ptr1.C)
  set(target "${curr_dir}-${file}.exe")
  add_executable(
    "${target}"
    "${file}"
  )
  target_link_libraries("${target}" PRIVATE gtest_main)
  add_test(NAME "${target}" COMMAND "${target}")
  gtest_discover_tests("${target}")
endforeach()

set(CMAKE_BUILD_TYPE "Release")
set(BENCHMARK_ENABLE_GTEST_TESTS OFF)
set(BENCHMARK_ENABLE_TESTING OFF)
FetchLibrary(
  https://github.com/google/benchmark.git
  main
)

set(file "scoped_ptr1_bm.C")
set(target "${curr_dir}-${file}.exe")
add_executable(
  "${target}"
  "${file}"
)

target_link_libraries(
  "${target}"
  benchmark::benchmark)
