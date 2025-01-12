cmake_minimum_required(VERSION 3.20.0)

project(IMGUI)

set(CMAKE_CXX_STANDARD 17)

message(STATUS "CMAKE_CURRENT_LIST_DIR : ${CMAKE_CURRENT_LIST_DIR}")

find_package(glfw3 CONFIG REQUIRED)

file(GLOB IMGUI_SOURCES ${CMAKE_CURRENT_LIST_DIR}/*.cpp)
file(GLOB IMGUI_HEADERS ${CMAKE_CURRENT_LIST_DIR}/*.h)

file(GLOB_RECURSE IMGUI_BACKEND_FILES
backends/imgui_impl_glfw*
backends/imgui_impl_opengl3*
)

add_library(IMGUI STATIC ${IMGUI_SOURCES} ${IMGUI_HEADERS}
${IMGUI_BACKEND_FILES}
)

target_include_directories(IMGUI PUBLIC ${CMAKE_CURRENT_LIST_DIR})
target_link_libraries(IMGUI PUBLIC glfw)
set(IMGUI_INCLUDE_DIRS ${CMAKE_CURRENT_LIST_DIR} ${CMAKE_CURRENT_LIST_DIR}/backends PARENT_SCOPE)
message(STATUS "IMGUI_INCLUDE_DIRS : ${IMGUI_INCLUDE_DIRS}")
