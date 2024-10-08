set(CMAKE_INCLUDE_CURRENT_DIR ON)

include(configure.cmake)

if(WIN32)
    add_definitions(-MT)
endif(WIN32)

add_definitions(-DPAL_STDCPP_COMPAT)

include_directories(${ROOT_DIR}/src/SOS/inc)

set(SOURCES
    hostcoreclr.cpp
    extensions.cpp
)

if(WIN32 AND NOT CLR_CMAKE_HOST_ARCH_ARM64 AND NOT CLR_CMAKE_HOST_ARCH_ARM)
    list(APPEND SOURCES
        hostdesktop.cpp
    )
endif(WIN32 AND NOT CLR_CMAKE_HOST_ARCH_ARM64 AND NOT CLR_CMAKE_HOST_ARCH_ARM)

if(CLR_CMAKE_HOST_UNIX)
    add_definitions(-DHOST_UNIX)
else(CLR_CMAKE_HOST_UNIX)
    add_definitions(-DHOST_WINDOWS)
endif(CLR_CMAKE_HOST_UNIX)

add_library(extensions STATIC ${SOURCES})
