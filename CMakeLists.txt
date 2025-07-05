cmake_minimum_required(VERSION 3.30)
project(imgui)
set(CMAKE_CXX_STANDARD 23)

set(IMGUI_SRC
    imgui.cpp
    imgui_draw.cpp
    imgui_tables.cpp
    imgui_widgets.cpp
)

set(IMGUI_BACKENDS
    backends/imgui_impl_vulkan.cpp
    backends/imgui_impl_glfw.cpp
)

add_library(${PROJECT_NAME} ${IMGUI_SRC} ${IMGUI_BACKENDS})

find_package(Vulkan REQUIRED)

target_link_libraries(${PROJECT_NAME}
    PRIVATE 
    Vulkan::Vulkan
    glfw
)

target_include_directories(${PROJECT_NAME} 
    PUBLIC
    backends/
)
