cmake_minimum_required(VERSION 3.4.1)

file(GLOB SILK_SOURCES silk/*.c)
file(GLOB SILK_SOURCES_FLOAT silk/float/*.c)
file(GLOB CELT_SOURCES celt/*.c)
file(GLOB OPUS_SOURCES src/*.c)

add_library(opus STATIC ${SILK_SOURCES} ${SILK_SOURCES_FLOAT} ${CELT_SOURCES} ${OPUS_SOURCES})

target_include_directories(opus PRIVATE silk silk/float celt src)
target_include_directories(opus PUBLIC include)

target_compile_definitions(opus PRIVATE OPUS_BUILD USE_ALLOCA)
