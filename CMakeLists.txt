cmake_minimum_required(VERSION 3.12.4)

project(libdict C)

set(CMAKE_CXX_STANDARD 14)

# set(CMAKE_C_FLAGS "${CMAKE_CXX_FLAGS_DEBUG} -Wall -Wno-unused-variable -Wno-unknown-pragmas -Wno-sign-conversion")

# dirs
set(SOURCE_DIR src)
set(HEADER_DIR include)

#
# libdict tree structures
#

# add SOURCE
file(GLOB_RECURSE SOURCE ${SOURCE_DIR}/*.c)
file(GLOB_RECURSE HEADER ${SOURCE_DIR}/*.h ${HEADER_DIR}/*.h)

add_library(dict ${LIBTYPE} ${SOURCE} ${HEADER})
include_directories(${HEADER_DIR})

# sanitizers
if(AUTOTOOLS3D_SANITIZERS)
    add_sanitizers(dict)
endif()

# target_link_libraries(dict PRIVATE igl::core igl::triangle ${LIBFIGLET} asls spdlog::spdlog_header_only)

# both for debug and release
# set_target_properties(dict PROPERTIES
#     VERSION ${LIBRARY_VERSION}
#     # OUTPUT_NAME at3d
#     LIBRARY_OUTPUT_DIRECTORY ${BLENDER_LIBRARY_DIR})
