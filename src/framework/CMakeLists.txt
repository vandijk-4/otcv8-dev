# Updated CMakeLists.txt

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Correctly detect platforms
if(APPLE)
    message(STATUS "Building on macOS")
elseif(WIN32)
    message(STATUS "Building on Windows")
else()
    message(STATUS "Building on Linux or other platform")
endif()

# Remove duplicate variables
set(SOURCE_FILES main.cpp utils.cpp)

# Set compiler flags appropriately
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -pedantic")

# Use find_package instead of hardcoded paths
find_package(SomeLibrary REQUIRED)
include_directories(${SomeLibrary_INCLUDE_DIRS})
add_executable(MyExecutable ${SOURCE_FILES})
target_link_libraries(MyExecutable ${SomeLibrary_LIBRARIES})
