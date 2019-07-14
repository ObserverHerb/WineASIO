cmake_minimum_required(VERSION 3.13)
project(wineasio_objects C)

set(CMAKE_C_FLAGS "-O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith")

set(WINE_INSTALL_PREFIX /usr)
set(WINE_FLAVOR wine)
set(WINE_INCLUDE_PATH ${WINE_INSTALL_PREFIX}/include/wine)

include_directories(${WINE_INCLUDE_PATH} ${WINE_INCLUDE_PATH}/windows)

add_library(interim OBJECT asio.c main.c regsvr.c)
