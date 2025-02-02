cmake_minimum_required (VERSION 3.0)

PROJECT(Chapter2)

set (CMAKE_CXX_STANDARD 11)

IF(EXISTS ${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
    include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
    conan_basic_setup()
ENDIF()

# Requires OpenCV
FIND_PACKAGE( OpenCV 4.0.0 REQUIRED )
MESSAGE("OpenCV version : ${OpenCV_VERSION}")

FIND_PACKAGE( Protobuf REQUIRED )
MESSAGE("Protobuf version : ${Protobuf_VERSION}")

MESSAGE("CONAN_LIBS : ${CONAN_LIBS}")
MESSAGE("Protobuf_LIBRARIES : ${Protobuf_LIBRARIES}")

ADD_EXECUTABLE( sample1 sample1.cpp )
TARGET_LINK_LIBRARIES( sample1 ${OpenCV_LIBS} ) 


ADD_EXECUTABLE( sample2 sample2.cpp )
TARGET_LINK_LIBRARIES( sample2 ${OpenCV_LIBS} )

ADD_EXECUTABLE( sample3 sample3.cpp )
TARGET_LINK_LIBRARIES( sample3 ${OpenCV_LIBS} )

ADD_EXECUTABLE( ${PROJECT_NAME} main.cpp )

TARGET_LINK_LIBRARIES( ${PROJECT_NAME} ${OpenCV_LIBS} ${CONAN_LIBS} ${Protobuf_LIBRARIES})
