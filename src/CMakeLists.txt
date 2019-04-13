cmake_minimum_required(VERSION 2.8)
project(ppc2c)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_SOURCE_DIR}/../cmake)

set(SOURCES
    main.cpp
)

find_package(IDA)

include_directories(${IDA_INCLUDE_DIR})
include_directories(${IDA_SDK_PATH}/ldr)
include_directories(${ELF_COMMON_PATH})

add_definitions(${IDA_DEFINITIONS})

add_library(ppc2c SHARED ${SOURCES})
target_link_libraries(ppc2c ${IDA_LIBRARIES})
set_target_properties(ppc2c PROPERTIES OUTPUT_NAME "ppc2c" PREFIX "" SUFFIX "${IDA_PLUGIN_EXT}")