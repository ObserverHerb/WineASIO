cmake_minimum_required(VERSION 3.13)
project(wineasio C)

option(WIN64 "Build for 64-bit Wine instead of 32-bit" OFF)

set(SCRIPTS_DIR "${CMAKE_SOURCE_DIR}/scripts")

add_subdirectory(src)
add_subdirectory(output)


## Download and extract header from Steinberg SDK

# determine whether install command should edit header for 64-bit support or just copy
if(WIN64)
	list(APPEND COPY_ASIO_HEADER "${SCRIPTS_DIR}/64bit_asio_header.sh")
	list(APPEND COPY_ASIO_HEADER "<SOURCE_DIR>/common/asio.h")
	list(APPEND COPY_ASIO_HEADER "${wineasio_objects_SOURCE_DIR}/asio.h")
else()
	list(APPEND COPY_ASIO_HEADER "cp")
	list(APPEND COPY_ASIO_HEADER "<SOURCE_DIR>/common/asio.h")
	list(APPEND COPY_ASIO_HEADER "${wineasio_objects_SOURCE_DIR}")
endif()

# download Steinberg SDK and use previous install command to put header in place
include(ExternalProject)
ExternalProject_Add(project_asio
	URL https://www.steinberg.net/asiosdk
	PREFIX ${CMAKE_SOURCE_DIR}/asiosdk
	CONFIGURE_COMMAND ""
	BUILD_COMMAND ""
	INSTALL_COMMAND ${COPY_ASIO_HEADER}
)
