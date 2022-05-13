cmake_minimum_required(VERSION 3.6)

project(xvcd_jlink)

set(SOURCE_FILES
        JlinkUtil.c
        io_jlink.c
        xvcd.c)

add_executable(xvcd_jlink ${SOURCE_FILES})

target_link_libraries(xvcd_jlink ${CMAKE_CURRENT_SOURCE_DIR}/JLinkARM.dll libws2_32.dll)