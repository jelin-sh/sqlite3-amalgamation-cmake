cmake_minimum_required(VERSION 3.1)

project(sqlite3_amalgamation)

set(CMAKE_CXX_STANDARD 17)

find_package(Threads REQUIRED)

add_library(sqlite3 STATIC sqlite3.c)
target_link_libraries(
    sqlite3 PUBLIC
    Threads::Threads
    ${CMAKE_DL_LIBS}
)
target_include_directories(sqlite3 PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

add_library(sqlite3::sqlite3 ALIAS sqlite3)
if(${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_CURRENT_SOURCE_DIR})
    add_subdirectory(test)
endif()
