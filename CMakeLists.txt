cmake_minimum_required(VERSION 3.10)
project(Water-Physics-Engine)

set(CMAKE_CXX_STANDARD 20)

# Find GLFW using pkg-config
find_package(PkgConfig REQUIRED)
pkg_check_modules(GLFW REQUIRED glfw3)

# Find OpenGL
find_package(OpenGL REQUIRED)

add_executable(WaterSim
    src/main.cpp
    src/glad.c
)

target_include_directories(WaterSim PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/include ${GLFW_INCLUDE_DIRS})
target_link_libraries(WaterSim ${GLFW_LIBRARIES} OpenGL::GL)