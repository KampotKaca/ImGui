project(imgui)

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

set(IMGUI_H
        imgui.h
        imgui_internal.h
        backends/imgui_impl_vulkan.h
        backends/imgui_impl_glfw.h
)

add_library(${PROJECT_NAME} ${IMGUI_SRC} ${IMGUI_BACKENDS})

target_sources(${PROJECT_NAME}
        PUBLIC
        FILE_SET HEADERS
        BASE_DIRS
        FILES ${IMGUI_H}
)

target_link_libraries(${PROJECT_NAME}
    PRIVATE
#        vulkan
#        glfw
)

target_include_directories(${PROJECT_NAME} 
    PUBLIC
    backends/
    ${Vulkan_INCLUDE_DIRS}
)
