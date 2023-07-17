cmake_minimum_required(VERSION 3.5)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(donut-game-maker LANGUAGES CXX)

find_package(Catch2 REQUIRED)

add_executable(tests test.cpp)

target_link_libraries(tests PRIVATE Catch2::Catch2WithMain)
include(CTest)
include(Catch)
catch_discover_tests(tests)


add_executable(donut-game-maker main.cpp)

find_package(SDL2 REQUIRED CONFIG REQUIRED COMPONENTS SDL2)
target_link_libraries(donut-game-maker PRIVATE SDL2::SDL2)
