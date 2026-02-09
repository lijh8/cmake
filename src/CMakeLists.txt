cmake_minimum_required(VERSION 3.31)
project(myapp VERSION 1.2.3)
set(CMAKE_C_COMPILER gcc) # .cpp
set(CMAKE_C_STANDARD 11) # .cpp
set(CMAKE_BUILD_RPATH_USE_ORIGIN TRUE) # boolean set(): TRUE/FALSE
set(CMAKE_INSTALL_RPATH "$ORIGIN/../lib")

# $ cmake -B build -S . -DENABLE_SANITIZERS=ON
option(ENABLE_SANITIZERS "Enable Sanitizers" OFF) # option(): ON/OFF
if (ENABLE_SANITIZERS)
    add_compile_options(-g)
    add_compile_options(-fsanitize=address,undefined)
    add_link_options(-fsanitize=address,undefined)
endif()

add_subdirectory(foo)
add_subdirectory(main)

# $ make -C build DESTDIR=~/myapp install
install(TARGETS foo)
install(TARGETS main)
#file(GLOB LIBRARIES ../lib/*.so*) # external libraries
#install(FILES ${LIBRARIES} DESTINATION lib)
