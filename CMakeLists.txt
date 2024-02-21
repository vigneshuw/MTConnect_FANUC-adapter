cmake_minimum_required(VERSION 3.16)
project(mtconnect_adapter)

set(CMAKE_CXX_STANDARD 17)

include_directories(.)

find_package( Threads )

add_executable(mtconnect_adapter
        minIni.c
        device_datum.cpp
        fanuc_axis.cpp
        fanuc_path.cpp
        service.cpp
        condition.cpp
        cutting_tool.cpp
        string_buffer.cpp
        logger.cpp
        client.cpp
        server.cpp
        adapter.cpp
        fanuc_adapter.cpp
        FanucAdapter.cpp
)
add_compile_definitions(FS30D)
find_library(fwlib32_location NAMES libfwlib32.so)
message(STATUS ${fwlib32_location})
add_library(fwlib32 STATIC IMPORTED)
set_target_properties(fwlib32 PROPERTIES IMPORTED_LOCATION ${fwlib32_location})
target_link_libraries(mtconnect_adapter fwlib32 ${CMAKE_THREAD_LIBS_INIT})

