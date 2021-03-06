cmake_minimum_required(VERSION 2.6)

project(imcl)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "./cmake")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
file(MAKE_DIRECTORY ${CMAKE_RUNTIME_OUTPUT_DIRECTORY})

set(OpenGL_GL_PREFERENCE GLVND)

find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)
find_package(GLEW REQUIRED)
find_package(ECL REQUIRED)

include_directories(
  ${OPENGL_INCLUDE_DIR}
  ${GLEW_INCLUDE_DIRS}
  ${ECL_INCLUDE_DIR}
  )

add_executable(imcl
  main.cpp
  imgui.cpp
  imgui_demo.cpp
  imgui_draw.cpp
  imgui_widgets.cpp
  imgui_impl_glfw.cpp
  imgui_impl_opengl3.cpp
  stb_image.cpp
  bindings.cpp)

target_link_libraries(imcl ${OPENGL_LIBRARY} glfw ${GLEW_LIBRARIES} ${ECL_LIBRARIES})
