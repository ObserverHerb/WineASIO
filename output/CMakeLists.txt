cmake_minimum_required(VERSION 3.13)
project(wineasio_dll C)

set(CMAKE_C_COMPILER winegcc)
set(CMAKE_C_FLAGS "-shared ${CMAKE_SOURCE_DIR}/wineasio.dll.spec -mno-cygwin")

set(WINE_INSTALL_PREFIX /usr)
set(WINE_FLAVOR wine)
set(WINE_INCLUDE_PATH ${WINE_INSTALL_PREFIX}/include/wine)
set(WINE_BIN_PATH ${WINE_INSTALL_PREFIX}/bin)
set(WINE_LIB_PATH ${WINE_INSTALL_PREFIX}/lib/${WINE_FLAVOR})

link_directories(${WINE_LIB_PATH}/wine)

find_library(JACK_LIBRARY NAMES jack)
find_library(UUID_LIBRARY NAMES uuid)

add_library(wineasio.dll SHARED)
set_target_properties(wineasio.dll PROPERTIES PREFIX "")
target_link_libraries(wineasio.dll interim ${JACK_LIBRARY} ${UUID_LIBRARY} odbc32 ole32 winmm)
