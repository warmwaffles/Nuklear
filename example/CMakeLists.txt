cmake_minimum_required(VERSION 3.20 FATAL_ERROR)

find_package(OpenGL)
find_package(GLEW)
find_package(GLFW)

# Assets

FILE(GLOB ICONS icon/*.png)
FILE(INSTALL ${ICONS} DESTINATION ../icon)

FILE(GLOB IMAGES images/*.png)
FILE(INSTALL ${IMAGES} DESTINATION ../images)

FILE(GLOB SKINS skins/*.png)
FILE(INSTALL ${SKINS} DESTINATION ../skins)

# Examples

add_executable(file_browser file_browser.c)
target_link_libraries(file_browser PUBLIC GLFW::GLFW)
target_link_libraries(file_browser PUBLIC OpenGL::GL)
target_link_libraries(file_browser PUBLIC m)
target_link_libraries(file_browser PUBLIC OpenGL::GLU)
target_link_libraries(file_browser PUBLIC GLEW::glew)
target_link_libraries(file_browser PUBLIC nuklear)

add_executable(extended extended.c)
target_link_libraries(extended PUBLIC GLFW::GLFW)
target_link_libraries(extended PUBLIC OpenGL::GL)
target_link_libraries(extended PUBLIC m)
target_link_libraries(extended PUBLIC OpenGL::GLU)
target_link_libraries(extended PUBLIC GLEW::glew)
target_link_libraries(extended PUBLIC nuklear)

add_executable(canvas canvas.c)
target_link_libraries(canvas PUBLIC GLFW::GLFW)
target_link_libraries(canvas PUBLIC OpenGL::GL)
target_link_libraries(canvas PUBLIC m)
target_link_libraries(canvas PUBLIC OpenGL::GLU)
target_link_libraries(canvas PUBLIC GLEW::glew)
target_link_libraries(canvas PUBLIC nuklear)

add_executable(skinning skinning.c)
target_link_libraries(skinning PUBLIC GLFW::GLFW)
target_link_libraries(skinning PUBLIC OpenGL::GL)
target_link_libraries(skinning PUBLIC m)
target_link_libraries(skinning PUBLIC OpenGL::GLU)
target_link_libraries(skinning PUBLIC GLEW::glew)
target_link_libraries(skinning PUBLIC nuklear)
