cmake_minimum_required(VERSION 3.13)
project(wineasio C)

option(WIN64 "Build for 64-bit Wine instead of 32-bit" OFF)

add_subdirectory(src)
add_subdirectory(output)
