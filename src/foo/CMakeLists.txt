file(GLOB SOURCES *.c *.cpp)
add_library(foo SHARED ${SOURCES})
target_include_directories(foo PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
set_target_properties(foo PROPERTIES VERSION ${PROJECT_VERSION} SOVERSION ${PROJECT_VERSION_MAJOR})
