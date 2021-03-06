cmake_minimum_required (VERSION 2.8.12)

# Project step I: Check dependencies
# ------------------------------------------------------------------------------------------------------
include(CheckCXXCompilerFlag)
include(CheckCXXSourceRuns)
#include(FindFreetype)

#if(${FREETYPE_FOUND})
#    message("Dependencies: Freetype found!")
#else()
#    message(FATAL_ERROR "Dependencies: Freetype not found!")
#endif()

#find_package(glfw3 3.2 REQUIRED)
#find_package(OpenGL REQUIRED)
#find_package( Eigen3 REQUIRED )
find_package(ITK REQUIRED )
include(${ITK_USE_FILE})
# Project step II: Set up project name
# ------------------------------------------------------------------------------------------------------
set(PROJ_MAIN_NAME rim)
ADD_DEFINITIONS(-arch x86_64
-std=c++11 # Or -std=c++0x
)

# Required libraries, flags, and include files for compiling and linking against STEAMLIKE (all targets)
#set(STEAMLIKE_EXTRA_LIBS "")
#set(STEAMLIKE_EXTRA_DEFS "")
#set(STEAMLIKE_EXTRA_INCS "")
#set(RESOURCES_PATH "${CMAKE_CURRENT_SOURCE_DIR}/resources" CACHE PATH "Setting resources path" FORCE)
set(${PROJ_MAIN_NAME}_PATH ${CMAKE_CURRENT_SOURCE_DIR})

#list(APPEND STEAMLIKE_EXTRA_INCS ${FREETYPE_INCLUDE_DIRS} ${EIGEN3_INCLUDE_DIR})
#list(APPEND STEAMLIKE_EXTRA_LIBS glfw ftgl ${OPENGL_gl_LIBRARY})

# Project step III: Add modules
# ------------------------------------------------------------------------------------------------------
add_subdirectory(modules)

# Project step IV: Add examples
# ------------------------------------------------------------------------------------------------------
add_subdirectory(samples)
