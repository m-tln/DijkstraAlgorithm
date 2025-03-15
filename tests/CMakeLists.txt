cmake_minimum_required(VERSION 3.14)
project(dijkstra_test LANGUAGES CXX)

find_package(GTest REQUIRED)

if (USE_BOOST_IN_TESTS)
    find_package(Boost REQUIRED)
endif()

add_executable(test_dijkstra
        test_dijkstra.cpp
)

target_link_libraries(test_dijkstra dijkstra_lib GTest::GTest GTest::Main)

if (USE_BOOST_IN_TESTS)
    target_link_libraries(test_dijkstra Boost::boost)
endif()

target_include_directories(test_dijkstra PRIVATE ../include)

enable_testing()
add_test(NAME DijkstraTests COMMAND test_dijkstra)