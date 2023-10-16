cmake_minimum_required(VERSION 3.21)

set(CMAKE_CXX_STANDARD 17)
project(imgui)


set(SOURCES
        imgui.cpp
        imgui_demo.cpp
        imgui_draw.cpp
        imgui_widgets.cpp
        imgui_tables.cpp
        #        imgui_impl_glfw.cpp
        #        imgui_impl_opengl3.cpp
)

set(HEADERS
        imgui.h
        imconfig.h
        imgui_internal.h
        imstb_rectpack.h
        imstb_textedit.h
        imstb_truetype.h
        #        imgui_impl_glfw.h
        #        imgui_impl_opengl3.h
)

add_library(${PROJECT_NAME} STATIC ${SOURCES} ${HEADERS})

if(WIN32)
    target_compile_definitions(${PROJECT_NAME} PRIVATE
            #        IMGUI_API=__declspec\(dllexport\)
    )
endif()
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

#find_package(OpenGL REQUIRED)
#target_link_libraries(${PROJECT_NAME} glfw OpenGL::GL)