cmake_minimum_required(VERSION 3.6)
project(untitled)

# Incorporating Into An Existing CMake Project
# CMake to download GoogleTest as part of the build's configure step.
include(FetchContent)
FetchContent_Declare(
        googletest
        # Specify the commit you depend on and update it regularly. (latest googletest commit - October 19, 2022)
        URL https://github.com/google/googletest/archive/e07617d6c692a96e126f11f85c3e38e46b10b4d0.zip
)
# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

# Linking against gtest

# Set source files for RELEASE target
set(RELEASE_SOURCE_FILES TicTacToe.cpp TicTacToeMain.cpp)

# Set source files for DEBUG target
set(DEBUG_SOURCE_FILES TicTacToe.cpp TicTacToeTests.cpp)

# Create RELEASE target
add_executable(ttt ${RELEASE_SOURCE_FILES})

# Create DEBUG target
add_executable(ttt_debug ${DEBUG_SOURCE_FILES})

# Link library
target_link_libraries(ttt_debug gtest)