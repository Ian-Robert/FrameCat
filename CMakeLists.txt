cmake_minimum_required (VERSION 3.10)

project ("FrameCat")

add_executable (FrameCat "src/main.cpp")

target_include_directories (FrameCat PUBLIC "include")