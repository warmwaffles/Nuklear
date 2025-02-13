cmake_minimum_required(VERSION 3.20 FATAL_ERROR)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

project(nuklear VERSION 4.8.6 LANGUAGES C)

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE DEBUG)
endif(NOT CMAKE_BUILD_TYPE)

set(CMAKE_C_FLAGS "-std=c99 -Wall -Wextra -Wpedantic -Wuninitialized")
set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS} -g")
set(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS} -O3")

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set(SOURCES
    src/nuklear_9slice.c
    src/nuklear_buffer.c
    src/nuklear_button.c
    src/nuklear_chart.c
    src/nuklear_color.c
    src/nuklear_color_picker.c
    src/nuklear_combo.c
    src/nuklear_context.c
    src/nuklear_contextual.c
    src/nuklear_draw.c
    src/nuklear_edit.c
    src/nuklear_font.c
    src/nuklear_group.c
    src/nuklear_image.c
    src/nuklear_input.c
    src/nuklear_layout.c
    src/nuklear_list_view.c
    src/nuklear_math.c
    src/nuklear_menu.c
    src/nuklear_page_element.c
    src/nuklear_panel.c
    src/nuklear_pool.c
    src/nuklear_popup.c
    src/nuklear_progress.c
    src/nuklear_property.c
    src/nuklear_scrollbar.c
    src/nuklear_selectable.c
    src/nuklear_slider.c
    src/nuklear_string.c
    src/nuklear_style.c
    src/nuklear_table.c
    src/nuklear_text.c
    src/nuklear_text_editor.c
    src/nuklear_toggle.c
    src/nuklear_tooltip.c
    src/nuklear_tree.c
    src/nuklear_utf8.c
    src/nuklear_util.c
    src/nuklear_vertex.c
    src/nuklear_widget.c
    src/nuklear_window.c
)

add_compile_definitions(NK_INCLUDE_DEFAULT_FONT=1)
add_compile_definitions(NK_INCLUDE_FONT_BAKING=1)
add_compile_definitions(NK_INCLUDE_VERTEX_BUFFER_OUTPUT=1)
add_compile_definitions(NK_INCLUDE_DEFAULT_ALLOCATOR=1)
add_compile_definitions(NK_INCLUDE_STANDARD_IO=1)
add_compile_definitions(NK_INCLUDE_FIXED_TYPES=1)

include_directories(include)
add_library(nuklear STATIC ${SOURCES})

target_include_directories(nuklear
    PUBLIC
        $<INSTALL_INTERFACE:include>
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/src
)

export(TARGETS nuklear FILE nuklear_config.cmake)

add_subdirectory(example)
