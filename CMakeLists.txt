﻿cmake_minimum_required(VERSION 3.8)
project (TaoMath C CXX)

SET(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/CMakeModules)

# use c++11
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
# use test
enable_testing()

if (NOT PROJECT_BINARY_DIR)
	set(PROJECT_BINARY_DIR build)
endif()

set (EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/run)
set (LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/run)

if (NOT CMAKE_BUILD_TYPE) 
    set(CMAKE_BUILD_TYPE "Release")
endif()
message("Build Type " ${CMAKE_BUILD_TYPE})

include_directories(${PROJECT_SOURCE_DIR})

set_property(GLOBAL PROPERTY USE_FOLDERS ON)
add_subdirectory(TaoMath)

if (NOT CMAKE_NO_BUILD_TEST) 
    add_subdirectory(test)
endif()
