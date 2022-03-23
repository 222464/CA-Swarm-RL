cmake_minimum_required(VERSION 3.13)

project(CA_Swarm_RL)
 
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/CMake")

if(NOT CMAKE_BUILD_TYPE)
    message("CMAKE_BUILD_TYPE not set, setting it to Release")
    set(CMAKE_BUILD_TYPE Release)
endif()
message(STATUS "Build type: ${CMAKE_BUILD_TYPE}")


############################################################################
# Add SFML

find_package(SFML 2.5 COMPONENTS system window graphics)

if(SFML_FOUND)
    message(STATUS "Found existing SFML in ${SFML_INCLUDE_DIR}")
    message(STATUS "SFML dependencies: ${SFML_DEPENDENCIES}")
    message(STATUS "SFML libraries: ${SFML_LIBRARIES}")
endif()

############################################################################
#

set(CA_SWARM_RL_SRC
    "source/Swarm_Test.cpp"
    "source/swarm/Swarm.cpp"
)

add_executable(CA_Swarm_RL ${CA_SWARM_RL_SRC})

set_property(TARGET CA_Swarm_RL PROPERTY CXX_STANDARD 14)
set_property(TARGET CA_Swarm_RL PROPERTY CXX_STANDARD_REQUIRED ON)

target_include_directories(CA_Swarm_RL PUBLIC ${SFML_INCLUDE_DIR})
target_link_libraries(CA_Swarm_RL ${SFML_LIBRARIES} ${SFML_DEPENDENCIES})
 
