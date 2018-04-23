project(sqlite_qt)
cmake_minimum_required(VERSION 3.10)

set(CMAKE_AUTOSTATICPLUGINS ON)

if(${CMAKE_VERSION} VERSION_GREATER_EQUAL "3.9.0" AND ${CMAKE_VERSION} VERSION_LESS "3.11.0")
  # Workaround bug in AUTOSTATICPLUGINS support introduced in the 3.9.0 upgrade, see
  # https://github.com/Alexpux/MINGW-packages/issues/3545#issuecomment-381339386
  set(CMAKE_AUTORCC ON)
endif()

find_package(Qt5 5.10 REQUIRED COMPONENTS Sql)

add_executable(${PROJECT_NAME} main.cpp dbmanager.cpp dbmanager.h)
target_include_directories(${PROJECT_NAME} PRIVATE .)
target_link_libraries(${PROJECT_NAME} PRIVATE Qt5::Sql)
