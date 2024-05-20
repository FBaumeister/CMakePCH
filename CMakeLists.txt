cmake_minimum_required(VERSION 3.22)


#######################################################################################################################
# Cpp Standard
#######################################################################################################################
if (NOT DEFINED CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 20)
endif()
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
#######################################################################################################################

project(PCHExample
                DESCRIPTION "Some Example for PCH usage"
                LANGUAGES CXX)

add_executable(App main.cpp)
target_precompile_headers(App PUBLIC $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/PCH.hpp>)

# Some general flag for PCH usage
set(CMAKE_PCH_INSTANTIATE_TEMPLATES ON) # Clang only but useful.