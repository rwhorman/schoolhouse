project(median_temp LANGUAGES CXX)

# The solution to the exercise is ecapsulated in an object file
# to be included in a cli for interactive use, and test driver
#
add_library(median_temp OBJECT median_temp.cpp)

# CLI (Command-line Interface) for interactively playing with the 
# solution to the exercise
add_executable(median_temp_cli cli.cpp $<TARGET_OBJECTS:median_temp>)

# Unit test driver
add_executable(median_temp_test test.cpp $<TARGET_OBJECTS:median_temp>)
target_link_libraries(median_temp_test test_catch_main)
target_include_directories(median_temp_test PUBLIC ${TEST_CATCH_INCLUDE_DIR})
add_test(pppcpp-chp04-02-median_temp_test median_temp_test)
