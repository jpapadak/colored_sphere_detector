cmake_minimum_required (VERSION 3.1)
project (colored_sphere_detector)

set (CMAKE_VERBOSE_MAKEFILE ON)
set (CMAKE_CXX_STANDARD 11)

include_directories (include)

find_package (OpenCV 3 REQUIRED)
find_package (OpenMP)

if (OPENMP_FOUND)
    set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
    set (CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${OpenMP_EXE_LINKER_FLAGS}")
endif()

add_executable (${PROJECT_NAME} 
    src/main.cpp)

target_link_libraries (${PROJECT_NAME}
    ${OpenCV_LIBRARIES})