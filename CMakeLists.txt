cmake_minimum_required(VERSION 3.10)

project(CloudSeedCore VERSION 1.0)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_subdirectory(DSP)

add_executable(CloudSeedDemo
    PluginProcessor.cpp
)

target_compile_definitions(CloudSeedCore PUBLIC
    BUFFER_SIZE=1024
    MAX_STR_SIZE=32
)

if(WIN32)
    target_compile_definitions(CloudSeedCore PRIVATE NOMINMAX WIN32_LEAN_AND_MEAN)
endif()

target_link_libraries(CloudSeedDemo PRIVATE CloudSeedCore)
