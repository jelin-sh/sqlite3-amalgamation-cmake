cmake_minimum_required(VERSION 3.1)

project(sqlite3_test)

set(CMAKE_CXX_STANDARD 17)

add_executable(sqlite3_test shell.c)
target_link_libraries(sqlite3_test sqlite3::sqlite3)
