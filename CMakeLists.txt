cmake_minimum_required (VERSION 3.10)

project ("FrameCat")

add_executable (FrameCat "src/main.cpp")

set(RAYLIB_DIR "${CMAKE_SOURCE_DIR}/dependencies/raylib")

target_include_directories (FrameCat PRIVATE "${RAYLIB_DIR}/include")

target_link_directories (FrameCat PRIVATE "${RAYLIB_DIR}/lib")

target_link_libraries (FrameCat PRIVATE raylib opengl32 winmm gdi32 user32 shell32)

add_custom_command(TARGET FrameCat POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    "${RAYLIB_DIR}/lib/raylib.dll"
    $<TARGET_FILE_DIR:FrameCat>
    COMMENT "Copying raylib.dll to binary directory..."
)