CMAKE_MINIMUM_REQUIRED(VERSION 3.8)
PROJECT(skin_procession C CXX)

################################################################################
# Compiler and linker options
ADD_DEFINITIONS(-Wall -DWIN32_LEAN_AND_MEAN -DUNICODE)

SET(CMAKE_AUTOMOC ON)
SET(CMAKE_AUTORCC ON) 
SET(CMAKE_CXX_STANDARD 11) 

################################################################################
# Sources and libraries
 
 
if(CMAKE_CURRENT_SOURCE_DIR STREQUAL CMAKE_SOURCE_DIR)
    find_package(OpenCV 3 REQUIRED)
endif()


FIND_PACKAGE(Qt5 COMPONENTS Core Widgets Xml Gui      REQUIRED)
qt5_wrap_ui(UI_HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/resource/cacheentrydetail.ui)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_BINARY_DIR})
LINK_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}/3rdparty/ChartDirector/lib/)
################################################################################
# Compile target
ADD_EXECUTABLE ( ${PROJECT_NAME} 

 main.cpp)
# https://www.kdab.com/using-cmake-with-qt-5/
qt5_use_modules(${PROJECT_NAME} Core Widgets Gui Xml) 
TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${OpenCV_LIBS})
