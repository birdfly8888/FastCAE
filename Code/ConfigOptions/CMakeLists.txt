CMAKE_MINIMUM_REQUIRED(VERSION 3.18.1 FATAL_ERROR)
SET(PROJECTNAME ConfigOptions)
PROJECT(${PROJECTNAME})
ADD_DEFINITIONS("-DCONFIGOPTIONS_API")

#Qt
IF(NOT DEFINED Qt5_DIR)
	SET(Qt5_DIR "Qt5_DIR-NOTFOUND" CACHE PATH "Qt5_DIR")
	MESSAGE(FATAL_ERROR "Qt5_DIR is null, please find Qt5_config.cmake file position!~")
ENDIF()

FILE(GLOB SRC_H_FILES "*.h")
FILE(GLOB SRC_CPP_FILES "*.cpp")

SET(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${TOP_PROJECT_SOURCE_DIR}/../output/bin_d)    
SET(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${TOP_PROJECT_SOURCE_DIR}/../output/bin) 
SET(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${TOP_PROJECT_SOURCE_DIR}/../output/bin_d)   
SET(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${TOP_PROJECT_SOURCE_DIR}/../output/bin) 

INCLUDE_DIRECTORIES(${TOP_PROJECT_SOURCE_DIR})

FIND_PACKAGE(Qt5 COMPONENTS Core Xml Widgets REQUIRED)
SET(CMAKE_AUTOMOC ON)
SOURCE_GROUP("Generated Files" FILES "${TOP_PROJECT_BINARY_DIR}/${PROJECTNAME}/${PROJECTNAME}_autogen/mocs_compilation.cpp")

ADD_LIBRARY(${PROJECTNAME} SHARED ${SRC_H_FILES} ${SRC_CPP_FILES})

TARGET_LINK_LIBRARIES(${PROJECTNAME} Qt5::Core Qt5::Xml Qt5::Widgets)
TARGET_LINK_LIBRARIES(${PROJECTNAME} debug "${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG}/Settings${CMAKE_DEBUG_POSTFIX}.lib"     optimized "${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE}/Settings${CMAKE_RELEASE_POSTFIX}.lib"
									 debug "${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG}/PythonModule${CMAKE_DEBUG_POSTFIX}.lib" optimized "${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE}/PythonModule${CMAKE_RELEASE_POSTFIX}.lib"
									 debug "${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG}/DataProperty${CMAKE_DEBUG_POSTFIX}.lib" optimized "${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE}/DataProperty${CMAKE_RELEASE_POSTFIX}.lib"
									 debug "${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG}/BCBase${CMAKE_DEBUG_POSTFIX}.lib"       optimized "${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE}/BCBase${CMAKE_RELEASE_POSTFIX}.lib"
									 debug "${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG}/Material${CMAKE_DEBUG_POSTFIX}.lib"     optimized "${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE}/Material${CMAKE_RELEASE_POSTFIX}.lib")
ADD_DEPENDENCIES(${PROJECTNAME} Material)