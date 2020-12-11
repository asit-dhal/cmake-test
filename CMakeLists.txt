cmake_minimum_required(VERSION 3.15)

project(InstallHelloWorld)

add_library(InstallHelloWorld hello_world.cpp)
set_target_properties(InstallHelloWorld PROPERTIES PREFIX "" SUFFIX "")
#set_property(TARGET InstallHelloWorld PROPERTY PUBLIC_HEADER ${CMAKE_CURRENT_SOURCE_DIR}/hello_world.h)

add_library(InstallHelloWorldShared SHARED hello_world.cpp)
set_target_properties(InstallHelloWorldShared PROPERTIES PREFIX "" SUFFIX "")
#set_property(TARGET InstallHelloWorldShared PROPERTY PUBLIC_HEADER ${CMAKE_CURRENT_SOURCE_DIR}/hello_world.h)

add_executable(Main main.cpp)
set_target_properties(Main PROPERTIES PREFIX "" SUFFIX "")

set(CMAKE_INSTALL_DEFAULT_TARGET_ARCHIVE_PERMISSIONS OWNER_READ OWNER_EXECUTE)
set(CMAKE_INSTALL_DEFAULT_TARGET_LIBRARY_PERMISSIONS OWNER_READ OWNER_EXECUTE GROUP_READ)
set(CMAKE_INSTALL_DEFAULT_TARGET_RUNTIME_PERMISSIONS OWNER_READ OWNER_EXECUTE GROUP_READ GROUP_EXECUTE)

set(CMAKE_INSTALL_LIBDIR "${CMAKE_BINARY_DIR}/lib")
set(CMAKE_INSTALL_BINDIR "${CMAKE_BINARY_DIR}/bin")

install(TARGETS InstallHelloWorld ARCHIVE)
install(TARGETS InstallHelloWorldShared LIBRARY)
install(TARGETS Main RUNTIME)
