cmake_minimum_required(VERSION 2.8.0)

if (DEFINED UNIX)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fPIC")
endif(DEFINED UNIX)

SET(TARGET qt-json)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR})

ADD_LIBRARY(${TARGET} json.cpp)

qtX_use_modules(${TARGET} Core)

set_target_properties(${TARGET} PROPERTIES AUTOMOC FALSE)

if(BUILD_SHARED_LIBS)
    set_target_properties(${TARGET} PROPERTIES
                          DEFINE_SYMBOL QTJSON_MAKEDLL
                          PUBLIC_HEADER "json.h"
                          )
    target_link_libraries(${TARGET} ${QT_LIBRARIES})
else()
    add_definitions(-DQTJSON_STATIC)
endif()
