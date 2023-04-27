cmake_path(GET CMAKE_CURRENT_BINARY_DIR FILENAME curr_dir)

file(GLOB files "*.C")
foreach(file ${files})
    cmake_path(GET file FILENAME file)
    set(target "${curr_dir}-${file}.exe")
    add_executable(
        "${target}"
        "${file}"
    )
endforeach()