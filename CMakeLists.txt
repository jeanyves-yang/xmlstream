cmake_minimum_required(VERSION 2.6)
PROJECT(xmlstream)

set(XMLSTREAM_BUILD_SHARED_LIBS ${BUILD_SHARED_LIBS})

#QtXML lib
find_package(Qt4 COMPONENTS QtXml)
if ( NOT QT_FOUND)
message(FATAL_ERROR "Package Qt not found!")
endif()
 if ( NOT QT_QTXML_FOUND )
  message(FATAL_ERROR " QtXml required, but not found!")
endif()

include(${QT_USE_FILE})
include_directories(${QT_INCLUDES})

if(QT_IS_STATIC) 
  option(BUILD_SHARED_LIBS "Build xmlstream with shared libraries." OFF)
else()
  option(BUILD_SHARED_LIBS "Build xmlstream with shared libraries." ON)
endif()
set(xmlstream_BUILD_SHARED_LIBS ${BUILD_SHARED_LIBS})


if(xmlstream_BUILD_SHARED_LIBS)
  add_library(xmlstream SHARED XmlReader.cxx XmlWriter.cxx)
else()
  add_library(xmlstream STATIC XmlReader.cxx XmlWriter.cxx)
endif()
