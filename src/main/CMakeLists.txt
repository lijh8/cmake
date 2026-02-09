file(GLOB SOURCES *.c *.cpp)
add_executable(main ${SOURCES})
target_link_libraries(main PRIVATE foo)
