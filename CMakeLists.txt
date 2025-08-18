cmake_minimum_required(VERSION 3.20)
project(wasmbind-example)

add_subdirectory(wasmbind)

add_executable(main src/main.cpp)
target_link_libraries(main PRIVATE webbind::webbind)
set_target_properties(main PROPERTIES LINKER_LANGUAGE CXX SUFFIX .wasm LINK_FLAGS "-Wl,--no-entry,--allow-undefined,--export=main,--export-dynamic,--export-table,--import-memory,--export-memory,--strip-all")