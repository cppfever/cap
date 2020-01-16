cmake_minimum_required(VERSION 3.11 FATAL_ERROR)
project(cap)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# C++ macro definitions
#add_compile_definitions(NANOVG_GL2_IMPLEMENTATION)

# Always build dll
set(BUILD_SHARED_LIBS ON)
set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)

# Directory where exe,dll and static library saved
set(cap_BINARY_DIR ${CMAKE_BINARY_DIR}/bin-${CMAKE_BUILD_TYPE})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${cap_BINARY_DIR})
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${cap_BINARY_DIR})
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${cap_BINARY_DIR})

find_package(opengl REQUIRED)

SET(NANOGUI_BUILD_PYTHON OFF)
add_subdirectory(3dparty/nanogui)

include_directories(
    3dparty/nanogui/include/
    ${NANOGUI_EXTRA_INCS}
    )

add_executable(cap app/main.cpp)
target_link_libraries(cap nanogui)
