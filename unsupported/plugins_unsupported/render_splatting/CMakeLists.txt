# Copyright 2019-2020, Collabora, Ltd.
# SPDX-License-Identifier: BSL-1.0


set(SOURCES splatrenderer_plugin.cpp)

set(HEADERS splatrenderer.h splatrenderer_plugin.h)

set(RESOURCES splatrenderer.qrc)

add_library(render_splatting MODULE ${SOURCES} ${HEADERS} ${RESOURCES})

target_include_directories(render_splatting PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})
target_link_libraries(render_splatting PUBLIC common)

set_property(TARGET render_splatting PROPERTY FOLDER Plugins)

set_property(TARGET render_splatting PROPERTY RUNTIME_OUTPUT_DIRECTORY
                                              ${MESHLAB_PLUGIN_OUTPUT_DIR})

set_property(TARGET render_splatting PROPERTY LIBRARY_OUTPUT_DIRECTORY
                                              ${MESHLAB_PLUGIN_OUTPUT_DIR})

install(
    TARGETS render_splatting
    DESTINATION ${MESHLAB_PLUGIN_INSTALL_DIR}
    COMPONENT Plugins)
