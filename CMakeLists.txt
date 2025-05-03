cmake_minimum_required(VERSION 3.15)
project(HelloWorld)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# ------------------------------------------------------------------------------
# Vulkan (assumes environment variable VULKAN_SDK is set correctly)
# ------------------------------------------------------------------------------
find_package(Vulkan REQUIRED)

# ------------------------------------------------------------------------------
# GLFW (via pkg-config)
# ------------------------------------------------------------------------------
find_package(PkgConfig REQUIRED)
pkg_check_modules(GLFW REQUIRED glfw3)

# ------------------------------------------------------------------------------
# GLM (header-only, manually included)
# Assumes Homebrew install to /opt/homebrew/include
# ------------------------------------------------------------------------------
set(GLM_INCLUDE_DIR "/opt/homebrew/include")

# ------------------------------------------------------------------------------
# Include + Link
# ------------------------------------------------------------------------------
include_directories(
    ${Vulkan_INCLUDE_DIR}
    ${GLFW_INCLUDE_DIRS}
    ${GLM_INCLUDE_DIR}
)

link_directories(${GLFW_LIBRARY_DIRS})

add_executable(HelloWorld src/main.cpp)

target_link_libraries(HelloWorld
    ${Vulkan_LIBRARY}
    ${GLFW_LIBRARIES}
)
