  
cmake_minimum_required(VERSION 2.8)
project(intersection-a3)

## ECE650 Specific configuration start here
## Project specific configurations go here

# enable c++11 support
set (CMAKE_CXX_FLAGS "-std=c++11 -Wall ${CMAKE_CXX_FLAGS}")
set(CMAKE_INSTALL_PREFIX ${CMAKE_BINARY_DIR}/run)
# Enable clang-tidy with all the checks except fuchsia default arguments
# set(CMAKE_CXX_CLANG_TIDY "clang-tidy;-checks=*,-fuchsia-default-arguments")

# create the main executable
## add additional .cpp files if needed
add_executable(intersection-a2 intersection-a2.cpp parser.cpp graph.cpp)
add_executable(rgen rgen.cpp street.cpp)
add_executable(intersection-a3 intersection-a3.cpp)

# create the executable for tests
add_executable(tests test.cpp)
install(PROGRAMS intersection-a1.py DESTINATION bin)
install(TARGETS rgen intersection-a2 intersection-a3 RUNTIME DESTINATION bin)