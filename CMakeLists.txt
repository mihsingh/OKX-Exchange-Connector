cmake_minimum_required(VERSION 3.15)
project(OKX-Exchange-Connector)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_subdirectory(REST)
add_subdirectory(WebSocket)