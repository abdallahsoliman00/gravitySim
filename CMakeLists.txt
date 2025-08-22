cmake_minimum_required(VERSION 3.29.2)
project(GravitySim LANGUAGES CXX)

# Put the .exe file in the root directory
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR})

# Executable from src/main.cpp
add_executable(${PROJECT_NAME} src/main.cpp)

# === Local libraries ===
add_subdirectory(libs/glm)
add_subdirectory(src)

# === Include paths ===
target_include_directories(${PROJECT_NAME} PRIVATE
    ${CMAKE_SOURCE_DIR}/libs
    ${CMAKE_SOURCE_DIR}/libs/glfw/include
    ${CMAKE_SOURCE_DIR}/libs/glew/include
)

# === Link directories ===
target_link_directories(${PROJECT_NAME} PRIVATE
    ${CMAKE_SOURCE_DIR}/libs/glfw/lib      # where libglfw3.a lives
    ${CMAKE_SOURCE_DIR}/libs/glew/lib      # where glew32s.lib lives
)

# === Preprocessor defines for static GLEW ===
target_compile_definitions(${PROJECT_NAME} PRIVATE GLEW_STATIC)

# === Link libraries ===
target_link_libraries(${PROJECT_NAME} PRIVATE
    mylib
    glm::glm
    libglfw3.a
    libglew32.a
    opengl32
    gdi32
    user32
    shell32
)
