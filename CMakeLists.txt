cmake_minimum_required(VERSION 3.7.2)
project(termiwin VERSION 1.2.1)

# Dirs
set (MAIN_SRC_DIR "${CMAKE_CURRENT_SOURCE_DIR}/src/")
set (MAIN_INC_DIR "${CMAKE_CURRENT_SOURCE_DIR}/include/")

add_library(termiwin STATIC "src/termiWin.c")
target_include_directories(termiwin PUBLIC "include")

if (TERMIWIN_DONOTREDEFINE)
	target_compile_definitions(termiwin PUBLIC "-DTERMIWIN_DONOTREDEFINE")
endif (TERMIWIN_DONOTREDEFINE)
