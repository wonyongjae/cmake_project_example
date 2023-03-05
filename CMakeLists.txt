cmake_minimum_required(VERSION 3.13)

# set project name
set(PROJECT_NAME cpp)
# set c++ version
set(CMAKE_CXX_STANDARD 17)

# select project
project(${PROJECT_NAME})
# select execute file path
add_executable(${PROJECT_NAME} src/main.cpp)

# build & compile
# 1
# cmake -Bbuild . -DCMAKE_BUILD_TYPE=[Debug|Release]
# 2
# cmake --build build --config Debug
# 3
# .\build\Debug\cpp.exe

# 컨트롤 쉬프트 p -> cmake 하면 config -> build 쌉가능

# 밑에 파란줄에 다 있음