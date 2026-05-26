set(TARGET main)
add_executable(${TARGET})
file(GLOB SOURCES CONFIGURE_DEPENDS *.c *.cpp)
target_sources(${TARGET} PRIVATE ${SOURCES})
target_link_libraries(${TARGET} PRIVATE foo)

if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU" AND CMAKE_CXX_COMPILER_VERSION VERSION_LESS 14)
    target_compile_options(${TARGET} PRIVATE -fmodules-ts)
endif()
