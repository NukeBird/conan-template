cmake_minimum_required(VERSION 3.22.0)

set(PROJECT_NAME cool_project)

project(${PROJECT_NAME})

add_definitions("-std=c++17")

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

file(GLOB_RECURSE PROJECT_SRC src/*.cpp src/*.hpp src/*.h)

add_executable(${PROJECT_NAME} ${PROJECT_SRC})
target_link_libraries(${PROJECT_NAME} ${CONAN_LIBS})