project(visualization.projectm)

cmake_minimum_required(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})
if(PACKAGE_CONFIG_PATH)
  set(ENV{PKG_CONFIG_PATH} ${PACKAGE_CONFIG_PATH})
endif()

find_package(kodi REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED)
find_package(ProjectM REQUIRED)

add_definitions(-DHAS_SDL_OPENGL)

set(INCLUDES ${OpenGL_INCLUDE_DIR}
             ${GLEW_INCLUDE_DIR}
             ${KODI_INCLUDE_DIR}
             ${PROJECTM_INCLUDE_DIRS})

set(DEPLIBS ${OPENGL_LIBRARIES}
            ${GLEW_LIBRARIES}
            ${PROJECTM_LIBS}
            ${extra_libs})

set(PM_SOURCES src/Main.cpp)

include_directories(${INCLUDES})

build_addon(visualization.projectm PM DEPLIBS)

include(CPack)
