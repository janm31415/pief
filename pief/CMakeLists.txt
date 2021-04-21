set(TBB_INCLUDE_DIR "C:/Program Files/TBB/include")
set(TBB_LIBRARY "C:/Program Files/TBB/lib/intel64/vc14")
set(TBB_DIR "C:/Program Files/TBB")
find_package(TBB REQUIRED)
include_directories(${TBB_INCLUDE_DIR})
link_directories(${TBB_LIBRARY})


set(IMGUI
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/imgui.h
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/imgui_impl_opengl3.h
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/imgui_impl_sdl.h
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/imgui_stdlib.h
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/dirent_portable.h
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/imguifilesystem.h
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/imgui.cpp
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/imgui_draw.cpp
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/imgui_demo.cpp
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/imgui_impl_opengl3.cpp
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/imgui_impl_sdl.cpp
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/imgui_stdlib.cpp
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/imgui_widgets.cpp
${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/imguifilesystem.cpp
)

set(HDRS
buffer_object.h
depthtexture.h
frame_buffer_object.h
logging.h
model.h
mouse_data.h
parse.h
pref_file.h
render_buffer.h
settings.h
shader.h
shader_program.h
texture.h
tokenize.h
trackball.h
vertex_array_object.h
view.h
    )
	
set(SRCS
buffer_object.cpp
depthtexture.cpp
frame_buffer_object.cpp
logging.cpp
model.cpp
parse.cpp
pref_file.cpp
render_buffer.cpp
main.cpp
settings.cpp
shader.cpp
shader_program.cpp
texture.cpp
tokenize.cpp
trackball.c
vertex_array_object.cpp
view.cpp
)

set(GLEW
glew.cpp
)

set(JSON
${CMAKE_CURRENT_SOURCE_DIR}/../json/json.hpp
)

set(CMAKE_C_FLAGS_DEBUG "/W4 /MP /GF /RTCu /Od /MDd /Zi")
set(CMAKE_CXX_FLAGS_DEBUG "/W4 /MP /GF /RTCu /Od /MDd /Zi")
set(CMAKE_C_FLAGS_RELEASE "/W4 /MP /GF /O2 /Ob2 /Oi /Ot /MD /Zi")
set(CMAKE_CXX_FLAGS_RELEASE "/W4 /MP /GF /O2 /Ob2 /Oi /Ot /MD /Zi")

include ("../jtk/jtk/jtk.cmake")

# general build definitions
add_definitions(-DNOMINMAX)
add_definitions(-D_UNICODE)
add_definitions(-DUNICODE)
add_definitions(-D_SCL_SECURE_NO_WARNINGS)
add_definitions(-D_CRT_SECURE_NO_WARNINGS)
add_definitions(-DIMGUI_IMPL_OPENGL_LOADER_GLEW)

add_executable(pief WIN32 ${HDRS} ${SRCS} ${GLEW} ${IMGUI} ${JSON})
source_group("Header Files" FILES ${hdrs})
source_group("Source Files" FILES ${srcs})
source_group("ThirdParty/Glew" FILES ${GLEW})
source_group("ThirdParty/ImGui" FILES ${IMGUI})
source_group("ThirdParty/json" FILES ${JSON})

 target_include_directories(pief
    PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/..
   	${CMAKE_CURRENT_SOURCE_DIR}/../glew/include
    ${CMAKE_CURRENT_SOURCE_DIR}/../glew/include/glew
    ${CMAKE_CURRENT_SOURCE_DIR}/../imgui_sdl/
    ${CMAKE_CURRENT_SOURCE_DIR}/../json/
    ${CMAKE_CURRENT_SOURCE_DIR}/../SDL2/include/
    )	
	
target_link_libraries(pief
    PRIVATE	
    tbb.lib
    SDL2
    SDL2main  
    opengl32.lib   
    lifting
    )	