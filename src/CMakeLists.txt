add_library(mylib my_funcs.cpp)

target_include_directories(
    mylib
    PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
)

target_include_directories(${PROJECT_NAME} PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
)
