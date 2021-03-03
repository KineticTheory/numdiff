# Numdiff with MSVC 2019 port

This is [numdiff-5.9.0](http://www.nongnu.org/numdiff/) with modifications to allow it to be built with MSVC 2019.

## See files in source directory for more information:

* [README](https://github.com/KineticTheory/numdiff/blob/master/README)
* [COPYING](https://github.com/KineticTheory/numdiff/blob/master/COPYING) - License details.
* [AUTHORS](https://github.com/KineticTheory/numdiff/blob/master/AUTHORS)

## Build Instructions

From a Visual Studio 2019 command prompt

```console
$ git clone https://github.com/KineticTheory/numdiff
$ mkdir build
$ cd build

$ cmake -DCMAKE_INSTALL_PREFIX=c:\tools ..\numdiff

-- Building for: Visual Studio 16 2019
-- Selecting Windows SDK version 10.0.18362.0 to target Windows 10.0.19043.
-- The C compiler identification is MSVC 19.28.29828.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: C:/Program Files (x86)/Microsoft Visual Studio/2019/Preview/VC/Tools/MSVC/14.28.29828/bin/Hostx64/x64/cl.exe - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Looking for string.h
-- Looking for string.h - found
-- Looking for 4 include files stdlib.h, ..., float.h
-- Looking for 4 include files stdlib.h, ..., float.h - found
-- Configuring done
-- Generating done
-- Build files have been written to: C:/work/x64-Debug/numdiff

$ cmake --build . --target install --config Release


Microsoft (R) Build Engine version 16.9.0-preview-21103-02+198f3f262 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

  Checking Build System
  Building Custom Rule C:/work/numdiff/CMakeLists.txt
  getopt.c
  linesplit.c
  ndselect.c
  getopt1.c
  bitvector.c
  ndselect.vcxproj -> C:\work\x64-Debug\numdiff\Release\ndselect.exe
  Building Custom Rule C:/work/numdiff/CMakeLists.txt
  analyze.c
  error.c
  cmpfns.c
  flags.c
  inout.c
  exitfail.c
  arith.c
  cmpbuf.c
  io.c
  main.c
  options.c
  side.c
  thrlist.c
  numutil.c
  util.c
  xmalloc.c
  bitvector.c
  xalloc-die.c
  getopt.c
  linesplit.c
  getopt1.c
  numdiff.vcxproj -> C:\work\x64-Debug\numdiff\Release\numdiff.exe
  Building Custom Rule C:/work/numdiff/CMakeLists.txt
  -- Install configuration: "Release"
  -- Installing: C:/Tools/bin/numdiff.exe
  -- Installing: C:/Tools/bin/ndselect.exe
```
