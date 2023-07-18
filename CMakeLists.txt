cmake_minimum_required(VERSION 3.5)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(donut-game-maker LANGUAGES CXX)

find_package(Catch2 REQUIRED)
find_package(glew REQUIRED)
find_package(SDL2 REQUIRED CONFIG REQUIRED COMPONENTS SDL2)

include(CTest)
include(Catch)

set(DONUT_ASSETS_PATH ${CMAKE_CURRENT_SOURCE_DIR}/assets)

configure_file(
    ${CMAKE_CURRENT_SOURCE_DIR}/donut.h.in
    ${CMAKE_CURRENT_SOURCE_DIR}/donut.h )

add_executable(tests test.cpp)
add_executable(donut-game-maker main.cpp)

target_link_libraries(donut-game-maker PRIVATE SDL2::SDL2)
target_link_libraries(donut-game-maker PRIVATE GLEW::glew)
target_link_libraries(tests PRIVATE Catch2::Catch2WithMain)

catch_discover_tests(tests)
