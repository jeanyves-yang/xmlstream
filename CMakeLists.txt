cmake_minimum_required(VERSION 2.6)
PROJECT(xmlstream)

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

add_library(xmlstream XmlReader.cxx XmlWriter.cxx)
