cmake_minimum_required(VERSION 3.15)

project(InstallHelloWorld)

add_library(InstallHelloWorld hello_world.cpp)
#set_property(TARGET InstallHelloWorld PROPERTY PUBLIC_HEADER ${CMAKE_CURRENT_SOURCE_DIR}/hello_world.h)

add_library(InstallHelloWorldShared SHARED hello_world.cpp)
#set_property(TARGET InstallHelloWorldShared PROPERTY PUBLIC_HEADER ${CMAKE_CURRENT_SOURCE_DIR}/hello_world.h)

add_executable(Main main.cpp)

set(CMAKE_INSTALL_DEFAULT_TARGET_ARCHIVE_PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE)
set(CMAKE_INSTALL_DEFAULT_TARGET_LIBRARY_PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ)
set(CMAKE_INSTALL_DEFAULT_TARGET_RUNTIME_PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE)

set(CMAKE_INSTALL_LIBDIR "/home/asit/proj/cmake-issues/install/build/lib")
set(CMAKE_INSTALL_BINDIR "/home/asit/proj/cmake-issues/install/build/bin")

install(TARGETS InstallHelloWorld ARCHIVE)
install(TARGETS InstallHelloWorldShared LIBRARY)
install(TARGETS Main RUNTIME)
