cmake_minimum_required(VERSION 3.7.2)
project(termiwin VERSION 1.2.1)

# Dirs
set (prefix ${CMAKE_INSTALL_PREFIX})
set (exec_prefix ${CMAKE_INSTALL_PREFIX})
set (MAIN_SRC_DIR "${CMAKE_CURRENT_SOURCE_DIR}/src/")
set (MAIN_INC_DIR "${CMAKE_CURRENT_SOURCE_DIR}/include/")
set (libpkgdata \${prefix}/lib)
set (incldir \${prefix}/include)

add_library(termiwin STATIC "src/termiWin.c")
target_include_directories(termiwin PUBLIC "include")

configure_file(libtermiwin.pc.in libtermiwin.pc @ONLY)

INSTALL(
    FILES ${CMAKE_CURRENT_SOURCE_DIR}/build/libtermiwin.pc
    DESTINATION ${libpkgdata}/pkgconfig
)
INSTALL(
    TARGETS termiwin
    DESTINATION ${libpkgdata}
)

if (TERMIWIN_DONOTREDEFINE)
	target_compile_definitions(termiwin PUBLIC "-DTERMIWIN_DONOTREDEFINE")
endif (TERMIWIN_DONOTREDEFINE)