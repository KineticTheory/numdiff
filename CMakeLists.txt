cmake_minimum_required(VERSION 3.18.0 FATAL_ERROR)
set(ndd "A diff program that compares floating point with relative error.")
project(numdiff DESCRIPTION ${ndd} VERSION 5.9.0 LANGUAGES C)

if(MSVC)
  set(USE_INTERNAL_GETOPT TRUE CACHE BOOL "Use Numdiff's version of getopt" FORCE)
  if(NOT CMAKE_C_FLAGS MATCHES "wd4996")
     string(APPEND CMAKE_C_FLAGS " /nologo /Gy /fp:precise /DWIN32 /D_WINDOWS /MP /DHAVE_CONFIG_H=1"
       " /wd4005 /wd4018 /wd4090 /wd4133 /wd4244 /wd4267 /wd4700 /wd4996")
     string(APPEND CMAKE_C_FLAGS_DEBUG " /MDd /Od /Zi /RTC1")
     string(APPEND CMAKE_C_FLAGS_RELEASE " /MD /O2")
  endif()  
  set( CMAKE_GNUtoMS ON CACHE BOOL "Compatibility flag for MinGW/MSVC." FORCE)
endif()

# Create config.h
include(CheckIncludeFile)
check_include_file("string.h" HAVE_STRING_H )
include(CheckIncludeFiles)
check_include_files("stdlib.h;stdarg.h;string.h;float.h" STDC_HEADERS LANGUAGE C) 
configure_file(${PROJECT_SOURCE_DIR}/config.h.in ${PROJECT_BINARY_DIR}/config.h )

# List of sources
if(USE_INTERNAL_GETOPT)
  set(getopt_sources
    getopt.c
    getopt1.c )
endif()

set(shared_sources
  bitvector.c
  linesplit.c )

set(numdiff_sources
  analyze.c
  arith.c
  cmpbuf.c
  cmpfns.c
  error.c
  exitfail.c
  flags.c
  inout.c
  io.c
  main.c
  numutil.c
  options.c
  side.c
  thrlist.c
  util.c
  xalloc-die.c
  xmalloc.c )

# Create targets
add_executable(numdiff ${numdiff_sources};${shared_sources};${getopt_sources})
add_executable(ndselect ndselect.c;${shared_sources};${getopt_sources})

foreach(tgt numdiff ndselect)
  target_include_directories(${tgt} PRIVATE 
    $<BUILD_INTERFACE:${PROJECT_BINARY_DIR}>
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}> )
endforeach()

# Install
install( TARGETS numdiff ndselect )
