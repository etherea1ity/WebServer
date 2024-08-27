# CMake 最低版本要求
cmake_minimum_required(VERSION 3.10)

# 项目名称
project(WebServer)

# 设置 C++ 标准
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# 包含项目的头文件目录
include_directories(${PROJECT_SOURCE_DIR})

# 包含MySQL的头文件目录
include_directories(/usr/local/include/mysql)

# 查找所有源文件
file(GLOB_RECURSE SOURCES "${PROJECT_SOURCE_DIR}/code/*.cpp")

# 添加可执行文件
add_executable(WebServer ${SOURCES})

# 链接线程库
target_link_libraries(WebServer pthread)

# 链接MySQL客户端库
target_link_libraries(WebServer mysqlclient)

# 复制资源文件到目标目录
file(COPY ${PROJECT_SOURCE_DIR}/resources DESTINATION ${CMAKE_BINARY_DIR})
