
cmake_minimum_required(VERSION 3.10)

project(GL VERSION 1.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

include_directories(include)

find_package(PkgConfig REQUIRED)
pkg_search_module(GLFW REQUIRED glfw3)

set(SOURCES
    src/main.cpp
    src/glad.c
)

add_executable(GL ${SOURCES})

include_directories(${GLFW_INCLUDE_DIRS})

target_link_libraries(GL ${GLFW_LIBRARIES})
if(POLICY CMP0072)
    cmake_policy(SET CMP0072 NEW)
endif()

find_package(OpenGL REQUIRED)
target_link_libraries(GL ${OPENGL_gl_LIBRARY} dl)
