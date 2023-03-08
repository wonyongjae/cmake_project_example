cmake_minimum_required(VERSION 3.13)

# set project name
set(PROJECT_NAME cmake_project_example)
# set c++ version
set(CMAKE_CXX_STANDARD 17)

# 1. create window by GLFW
set(WINDOW_NAME "CMake Project Example")
set(WINDOW_WIDTH 960)
set(WINDOW_HEIGHT 540)

# select project
project(${PROJECT_NAME})
# select execute file path
add_executable(${PROJECT_NAME} 
    src/main.cpp
    src/common.cpp src/common.h
    src/shader.cpp src/shader.h
    src/program.cpp src/program.h
    src/context.cpp src/context.h
    src/buffer.cpp src/buffer.h
    src/vertex_layout.cpp src/vertex_layout.h
    src/image.cpp src/image.h
    src/texture.cpp src/texture.h
    )
# build & compile
# 1. cmake -Bbuild . -DCMAKE_BUILD_TYPE=[Debug|Release]
# 2. cmake --build build --config Debug
# 3. .\build\Debug\cpp.exe
# 컨트롤 쉬프트 p -> cmake 하면 config -> build 쌉가능
# 밑에 파란줄에 다 있음


# Dependency 코드를 따로 뺀 파일을 include
include(Dependency.cmake)

# 우리 프로젝트에 include / lib 관련 옵션 추가
target_include_directories(${PROJECT_NAME} PUBLIC ${DEP_INCLUDE_DIR})
target_link_directories(${PROJECT_NAME} PUBLIC ${DEP_LIB_DIR})
target_link_libraries(${PROJECT_NAME} PUBLIC ${DEP_LIBS})

# 2. create window by GLFW
target_compile_definitions(${PROJECT_NAME} PUBLIC
    WINDOW_NAME="${WINDOW_NAME}"
    WINDOW_WIDTH=${WINDOW_WIDTH}
    WINDOW_HEIGHT=${WINDOW_HEIGHT}
    )

# Dependency들이 먼저 build 될 수 있게 관계 설정
add_dependencies(${PROJECT_NAME} ${DEP_LIST})