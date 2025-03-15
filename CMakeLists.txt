cmake_minimum_required(VERSION 3.14)
project(DijkstraProject LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(dijkstra_lib
        src/Graph.cpp
        src/Dijkstra.cpp
        src/Utils.cpp
        src/priority_queue/BinaryHeap.cpp
        src/priority_queue/FibonacciHeap.cpp
        src/priority_queue/SetWrapper.cpp
)

target_include_directories(dijkstra_lib PUBLIC include)

add_executable(dijkstra_example examples/basic_usage.cpp)
target_link_libraries(dijkstra_example dijkstra_lib)

option(USE_BOOST_IN_TESTS "Use Boost in tests" OFF)
add_subdirectory(tests)
