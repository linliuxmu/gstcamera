cmake_minimum_required(VERSION 2.6)

project(gstcamera)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

include(FindPkgConfig)

pkg_check_modules(GStreamer gstreamer-0.10)
pkg_check_modules(GStreamer_Video gstreamer-video-0.10)

include_directories(
    ${GStreamer_INCLUDE_DIRS}
    ${GStreamer_Video_INCLUDE_DIRS}
)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

add_definitions(-Wall)

add_executable(gstcamera gstcamera.cpp)
target_link_libraries(
    gstcamera
    ${GStreamer_LIBRARIES}
    ${GStreamer_Video_LIBRARIES}
)

install(TARGETS gstcamera RUNTIME DESTINATION /usr/bin)

