cmake_minimum_required(VERSION 3.18.1)
project(stuffmods)

add_library(stuffmods SHARED
    Menu.cpp
    imgui.cpp
    imgui_draw.cpp
    imgui_tables.cpp
    imgui_widgets.cpp
    imgui_impl_android.cpp
    imgui_impl_vulkan.cpp
)

add_library(dobby STATIC IMPORTED)
set_target_properties(dobby PROPERTIES
    IMPORTED_LOCATION ${CMAKE_SOURCE_DIR}/libdobby.a)

target_include_directories(stuffmods PRIVATE .)

target_compile_options(stuffmods PRIVATE -O2 -std=c++17)

target_link_libraries(stuffmods PRIVATE dobby log android z vulkan)
