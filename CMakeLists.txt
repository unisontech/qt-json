cmake_minimum_required(VERSION 2.8.0)

if (DEFINED UNIX)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fPIC")
endif(DEFINED UNIX)

SET(TARGET qt-json)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR})

ADD_LIBRARY(${TARGET} ${LIBRARY_TYPE} json.cpp)

qtX_use_modules(${TARGET} Core)

set_target_properties(${TARGET} PROPERTIES AUTOMOC FALSE)

target_link_libraries(${TARGET}
                      ${QT_LIBRARIES}
                     )
