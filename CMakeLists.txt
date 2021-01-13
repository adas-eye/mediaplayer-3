cmake_minimum_required(VERSION 3.16)
project(videowidget LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

find_package(Qt5 COMPONENTS Multimedia)
find_package(Qt5 COMPONENTS MultimediaWidgets)
find_package(Qt5 COMPONENTS Widgets)

set(HEADERS videoplayer.h)

set(SOURCES
    main.cpp
    videoplayer.cpp)

if(ANDROID)
    add_library(${PROJECT_NAME} SHARED
        ${HEADERS}
        ${SOURCES})
else()
    add_executable(${PROJECT_NAME} ${HEADERS} ${SOURCES})
endif()

target_link_libraries(${PROJECT_NAME} PUBLIC
    Qt5::Multimedia
    Qt5::MultimediaWidgets
    Qt5::Widgets)


