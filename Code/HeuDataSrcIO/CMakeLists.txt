CMAKE_MINIMUM_REQUIRED(VERSION 3.18.1 FATAL_ERROR)
SET(PROJECTNAME HeuDataSrcIO)
PROJECT(${PROJECTNAME})
ADD_DEFINITIONS("-DHEUDATASRCIO_LIBRARY")
#SET_PROPERTY(TARGET ${PROJECTNAME} PROPERTY FOLDER "Post")

#Qt
IF(NOT DEFINED Qt5_DIR)
	SET(Qt5_DIR "Qt5_DIR-NOTFOUND" CACHE PATH "Qt5_DIR")
	MESSAGE(SEND_ERROR "Qt5_DIR is null, please find Qt5_config.cmake file position!~")
ENDIF()
#VTK
IF(NOT DEFINED FASTCAE_VTK_INCLUDE)
	SET(FASTCAE_VTK_INCLUDE "FASTCAE_VTK_INCLUDE-NOTFOUND" CACHE PATH "FASTCAE_VTK_INCLUDE")
	MESSAGE(SEND_ERROR "FASTCAE_VTK_INCLUDE is null, please specified VTK include directory!~")
ENDIF()
IF(NOT DEFINED FASTCAE_VTK_LIBDIR)
	SET(FASTCAE_VTK_LIBDIR "FASTCAE_VTK_LIBDIR-NOTFOUND" CACHE PATH "FASTCAE_VTK_LIBDIR")
	MESSAGE(SEND_ERROR "FASTCAE_VTK_LIBDIR is null, please specified VTK release library directory!~")
ENDIF()
IF(NOT DEFINED FASTCAE_VTK_LIBDDIR)
	SET(FASTCAE_VTK_LIBDDIR "FASTCAE_VTK_LIBDDIR-NOTFOUND" CACHE PATH "FASTCAE_VTK_LIBDDIR")
	MESSAGE(SEND_ERROR "FASTCAE_VTK_LIBDDIR is null, please specified VTK debug library directory!~")
ENDIF()
IF(NOT DEFINED FASTCAE_VTK_BINDIR)
	SET(FASTCAE_VTK_BINDIR "FASTCAE_VTK_BINDIR-NOTFOUND" CACHE PATH "FASTCAE_VTK_BINDIR")
	MESSAGE(SEND_ERROR "FASTCAE_VTK_BINDIR is null, please specified VTK release dll directory!~")
ENDIF()
IF(NOT DEFINED FASTCAE_VTK_BINDDIR)
	SET(FASTCAE_VTK_BINDDIR "FASTCAE_VTK_BINDDIR-NOTFOUND" CACHE PATH "FASTCAE_VTK_BINDDIR")
	MESSAGE(SEND_ERROR "FASTCAE_VTK_BINDDIR is null, please specified VTK release dll directory!~")
ENDIF()
#OCC
IF(NOT DEFINED FASTCAE_OCC_INCLUDE)
	SET(FASTCAE_OCC_INCLUDE "FASTCAE_OCC_INCLUDE-NOTFOUND" CACHE PATH "FASTCAE_OCC_INCLUDE")
	MESSAGE(SEND_ERROR "FASTCAE_OCC_INCLUDE is null, please specified OCC include directory!~")
ENDIF()
IF(NOT DEFINED FASTCAE_OCC_LIBDIR)
	SET(FASTCAE_OCC_LIBDIR "FASTCAE_OCC_LIBDIR-NOTFOUND" CACHE PATH "FASTCAE_OCC_LIBDIR")
	MESSAGE(SEND_ERROR "FASTCAE_OCC_LIBDIR is null, please specified OCC release library directory!~")
ENDIF()
IF(NOT DEFINED FASTCAE_OCC_LIBDDIR)
	SET(FASTCAE_OCC_LIBDDIR "FASTCAE_OCC_LIBDDIR-NOTFOUND" CACHE PATH "FASTCAE_OCC_LIBDDIR")
	MESSAGE(SEND_ERROR "FASTCAE_OCC_LIBDDIR is null, please specified OCC debug library directory!~")
ENDIF()
IF(NOT DEFINED FASTCAE_OCC_BINDIR)
	SET(FASTCAE_OCC_BINDIR "FASTCAE_OCC_BINDIR-NOTFOUND" CACHE PATH "FASTCAE_OCC_BINDIR")
	MESSAGE(SEND_ERROR "FASTCAE_OCC_BINDIR is null, please specified OCC release dll directory!~")
ENDIF()
IF(NOT DEFINED FASTCAE_OCC_BINDDIR)
	SET(FASTCAE_OCC_BINDDIR "FASTCAE_OCC_BINDDIR-NOTFOUND" CACHE PATH "FASTCAE_OCC_BINDDIR")
	MESSAGE(SEND_ERROR "FASTCAE_OCC_BINDDIR is null, please specified OCC release dll directory!~")
ENDIF()
#CGNS
IF(NOT DEFINED FASTCAE_CGNS_INCLUDE)
	SET(FASTCAE_CGNS_INCLUDE "FASTCAE_CGNS_INCLUDE-NOTFOUND" CACHE PATH "FASTCAE_CGNS_INCLUDE")
	MESSAGE(SEND_ERROR "FASTCAE_CGNS_INCLUDE is null, please specified CGNS include directory!~")
ENDIF()
IF(NOT DEFINED FASTCAE_CGNS_LIBDIR)
	SET(FASTCAE_CGNS_LIBDIR "FASTCAE_CGNS_LIBDIR-NOTFOUND" CACHE PATH "FASTCAE_CGNS_LIBDIR")
	MESSAGE(SEND_ERROR "FASTCAE_CGNS_LIBDIR is null, please specified CGNS release library directory!~")
ENDIF()
IF(NOT DEFINED FASTCAE_CGNS_LIBDDIR)
	SET(FASTCAE_CGNS_LIBDDIR "FASTCAE_CGNS_LIBDDIR-NOTFOUND" CACHE PATH "FASTCAE_CGNS_LIBDDIR")
	MESSAGE(SEND_ERROR "FASTCAE_CGNS_LIBDDIR is null, please specified CGNS debug library directory!~")
ENDIF()
IF(NOT DEFINED FASTCAE_CGNS_BINDIR)
	SET(FASTCAE_CGNS_BINDIR "FASTCAE_CGNS_BINDIR-NOTFOUND" CACHE PATH "FASTCAE_CGNS_BINDIR")
	MESSAGE(SEND_ERROR "FASTCAE_CGNS_BINDIR is null, please specified CGNS release dll directory!~")
ENDIF()
IF(NOT DEFINED FASTCAE_CGNS_BINDDIR)
	SET(FASTCAE_CGNS_BINDDIR "FASTCAE_CGNS_BINDDIR-NOTFOUND" CACHE PATH "FASTCAE_CGNS_BINDDIR")
	MESSAGE(FATAL_ERROR "FASTCAE_CGNS_BINDDIR is null, please specified CGNS release dll directory!~")
ENDIF()

IF(NOT DEFINED FASTCAE_VTK_LIBDS)
	FILE(GLOB FASTCAE_VTK_LIBDS "${FASTCAE_VTK_LIBDDIR}/*.lib")
ENDIF()
IF(NOT DEFINED FASTCAE_VTK_LIBS)
	FILE(GLOB FASTCAE_VTK_LIBS "${FASTCAE_VTK_LIBDIR}/*.lib")
ENDIF()
IF(NOT DEFINED FASTCAE_CGNS_LIBDS)
	FILE(GLOB FASTCAE_CGNS_LIBDS "${FASTCAE_CGNS_LIBDDIR}/*.lib")
ENDIF()
IF(NOT DEFINED FASTCAE_CGNS_LIBS)
	FILE(GLOB FASTCAE_CGNS_LIBS "${FASTCAE_CGNS_LIBDIR}/*.lib")
ENDIF()
IF(NOT DEFINED FASTCAE_OCC_LIBDS)
	FILE(GLOB FASTCAE_OCC_LIBDS "${FASTCAE_OCC_LIBDDIR}/*.lib")
ENDIF()
IF(NOT DEFINED FASTCAE_OCC_LIBS)
	FILE(GLOB FASTCAE_OCC_LIBS "${FASTCAE_OCC_LIBDIR}/*.lib")
ENDIF()

FILE(GLOB SRC_H_FILES "*.h")
FILE(GLOB SRC_CPP_FILES "*.cpp")

SET(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${TOP_PROJECT_SOURCE_DIR}/../output/bin_d)    
SET(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${TOP_PROJECT_SOURCE_DIR}/../output/bin) 
SET(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${TOP_PROJECT_SOURCE_DIR}/../output/bin_d)   
SET(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${TOP_PROJECT_SOURCE_DIR}/../output/bin) 

INCLUDE_DIRECTORIES(${TOP_PROJECT_SOURCE_DIR}/SolutionDataIO
					${FASTCAE_VTK_INCLUDE}
					${FASTCAE_OCC_INCLUDE}
					${FASTCAE_CGNS_INCLUDE}
					${PROJECTNAME})

FIND_PACKAGE(Qt5 COMPONENTS Core Gui Widgets REQUIRED)
SET(CMAKE_AUTOMOC ON)
SOURCE_GROUP("Generated Files" FILES "${TOP_CMAKELISTS}/${PROJECTNAME}/${PROJECTNAME}_autogen/mocs_compilation.cpp")

ADD_LIBRARY(${PROJECTNAME} SHARED ${SRC_H_FILES} ${SRC_CPP_FILES})

TARGET_LINK_LIBRARIES(${PROJECTNAME} Qt5::Gui Qt5::Widgets Qt5::Core)
TARGET_LINK_LIBRARIES(${PROJECTNAME} debug "${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG}/SolutionDataIO${CMAKE_DEBUG_POSTFIX}.lib" optimized "${CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE}/SolutionDataIO${CMAKE_RELEASE_POSTFIX}.lib")
ADD_DEPENDENCIES(${PROJECTNAME} CurveAnalyse)

FOREACH(FASTCAE_VTK_LIBD ${FASTCAE_VTK_LIBDS})
	TARGET_LINK_LIBRARIES(${PROJECTNAME} debug ${FASTCAE_VTK_LIBD})
ENDFOREACH()	
FOREACH(FASTCAE_VTK_LIB ${FASTCAE_VTK_LIBS})
	TARGET_LINK_LIBRARIES(${PROJECTNAME} optimized ${FASTCAE_VTK_LIB})
ENDFOREACH()

FOREACH(FASTCAE_OCC_LIBD ${FASTCAE_OCC_LIBDS})
	TARGET_LINK_LIBRARIES(${PROJECTNAME} debug ${FASTCAE_OCC_LIBD})
ENDFOREACH()	
FOREACH(FASTCAE_OCC_LIB ${FASTCAE_OCC_LIBS})
	TARGET_LINK_LIBRARIES(${PROJECTNAME} optimized ${FASTCAE_OCC_LIB})
ENDFOREACH()

FOREACH(FASTCAE_CGNS_LIBD ${FASTCAE_CGNS_LIBDS})
	TARGET_LINK_LIBRARIES(${PROJECTNAME} debug ${FASTCAE_CGNS_LIBD})
ENDFOREACH()	
FOREACH(FASTCAE_CGNS_LIB ${FASTCAE_CGNS_LIBS})
	TARGET_LINK_LIBRARIES(${PROJECTNAME} optimized ${FASTCAE_CGNS_LIB})
ENDFOREACH()