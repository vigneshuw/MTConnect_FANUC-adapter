cmake_minimum_required(VERSION 3.16)
project(FANUCAdapter)

set(CMAKE_CXX_STANDARD 17)

# Threads
find_package( Threads )

# Include Directories
# FANUC
include_directories(fanuc)
include_directories(${CMAKE_SOURCE_DIR}/lib/FOCAS2)
# Adapter Source
include_directories(src)
# Libs
include_directories(${CMAKE_SOURCE_DIR}/lib/minIni)

# Executable
add_executable(FANUCAdapter
        fanuc/fanuc_adapter.cpp
        fanuc/FanucAdapter.cpp
        fanuc/fanuc_axis.cpp
        fanuc/fanuc_path.cpp
        src/device_datum.cpp
        src/logger.cpp
        src/client.cpp
        src/server.cpp
        src/adapter.cpp
        src/service.cpp
        src/condition.cpp
        src/cutting_tool.cpp
        src/string_buffer.cpp
        lib/minIni/minIni.c)

# Find and declare the FOCAS2 library for CMake
# Compile definitions
add_compile_definitions(FS30D)
find_library(fwlib32_location NAMES libfwlib32.so)
message(STATUS ${fwlib32_location})
add_library(fwlib32 STATIC IMPORTED)
set_target_properties(fwlib32 PROPERTIES IMPORTED_LOCATION ${fwlib32_location})
# Along with the pthread flag
target_link_libraries(FANUCAdapter PRIVATE fwlib32 ${CMAKE_THREAD_LIBS_INIT})
