cmake_minimum_required(VERSION 3.13.0) # need 3.13 for target_sources

project(TestMath CXX)

add_executable(${PROJECT_NAME} "")

target_sources(${PROJECT_NAME}
    PUBLIC 
    UnitTestMath.cpp
	UTMatrix.cpp
	UTVector2f.cpp
	UTVector3f.cpp
	UTVector4f.cpp
	UTCollisions.cpp)

# Needed for x64 architecture so it looks inside a lib64 repository
set_property(GLOBAL PROPERTY FIND_LIBRARY_USE_LIB64_PATHS TRUE)

find_package(CorgiTest)

target_link_libraries(${PROJECT_NAME}
    PRIVATE
    CorgiMath
    CorgiTest)

set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 20)

add_test(NAME TestMath COMMAND TestMath)