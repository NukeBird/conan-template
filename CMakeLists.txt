cmake_minimum_required(VERSION 3.22.0)

set(PROJECT_NAME cool_project)

project(${PROJECT_NAME})

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

file(GLOB_RECURSE PROJECT_SRC src/*.cpp src/*.hpp src/*.h)

add_executable(${PROJECT_NAME} ${PROJECT_SRC})
target_link_libraries(${PROJECT_NAME} ${CONAN_LIBS})

set_property(TARGET ${PROJECT_NAME} PROPERTY VS_DEBUGGER_WORKING_DIRECTORY "${CMAKE_SOURCE_DIR}")
set_target_properties(${PROJECT_NAME} PROPERTIES CXX_STANDARD 17 
                                       CXX_STANDARD_REQUIRED ON
                                       CXX_EXTENSIONS OFF)

if(WIN32)
    #Compile with -MT
    set_property(TARGET ${PROJECT_NAME} PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>") 
endif()