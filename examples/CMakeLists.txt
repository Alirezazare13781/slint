# Copyright © SixtyFPS GmbH <info@slint-ui.com>
# SPDX-License-Identifier: GPL-3.0-only OR LicenseRef-Slint-commercial
cmake_minimum_required(VERSION 3.19)
project(SlintExamples LANGUAGES CXX)

list(PREPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/../cmake")

find_package(OpenGLES2 QUIET)

if (NOT TARGET Slint::Slint)
    find_package(Slint REQUIRED)
    include(FetchContent)
endif()

add_subdirectory(printerdemo/cpp/)
if (SLINT_FEATURE_INTERPRETER)
    add_subdirectory(printerdemo/cpp_interpreted/)
endif()
add_subdirectory(printerdemo_old/cpp/)
add_subdirectory(todo/cpp/)
add_subdirectory(gallery/)
add_subdirectory(memory/)
if (SLINT_FEATURE_INTERPRETER AND SLINT_FEATURE_BACKEND_QT)
    add_subdirectory(qt_viewer/)
endif()
if (SLINT_FEATURE_INTERPRETER)
    add_subdirectory(iot-dashboard/)
endif()
if (OpenGLES2_FOUND AND SLINT_FEATURE_BACKEND_GL)
    add_subdirectory(opengl_underlay)
endif()
