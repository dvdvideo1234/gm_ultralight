﻿cmake_minimum_required (VERSION 3.8)
project (gmsv_ultralight CXX)
add_compile_definitions("GMMODULE")

#set ( CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON )
#set(TPN_WIN32 "/EHsc")
include_directories("./include")
link_directories("lib")
link_libraries(UltralightCore Ultralight WebCore)
#target_include_directories(
   # gmsv_ultralight
   # PUBLIC
   #     "include"
   # )
#set( SOURCE_LIB src )

add_library(gmsv_ultralight SHARED "src/gmsv_ultralight.cpp") #"include/dlfcn.h"
set(ultralight "gmsv_ultralight_")

if(WIN32)
	set_target_properties(gmsv_ultralight PROPERTIES OUTPUT_NAME "${ultralight}win64")
	add_compile_definitions("_AMD64_")
elseif(UNIX)
	set_target_properties(gmsv_ultralight PROPERTIES OUTPUT_NAME "${ultralight}linux64")
elseif(APPLE)
	set_target_properties(gmsv_ultralight PROPERTIES OUTPUT_NAME "${ultralight}osx64")
endif()