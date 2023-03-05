cmake_minimum_required(VERSION 3.13)

# set project name
set(PROJECT_NAME cmake_project_example)
# set c++ version
set(CMAKE_CXX_STANDARD 17)

# select project
project(${PROJECT_NAME})
# select execute file path
add_executable(${PROJECT_NAME} src/main.cpp)

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

# Dependency들이 먼저 build 될 수 있게 관계 설정
add_dependencies(${PROJECT_NAME} ${DEP_LIST})