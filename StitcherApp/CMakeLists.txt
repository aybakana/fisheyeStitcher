# CMakeList.txt : CMake project for StitcherApp, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

set(CMAKE_CXX_STANDARD 17)

set(OpenCV_DIR "D:\\Documents\\OpenCV\\opencv\\build\\install") # opencv installation location
find_package( OpenCV REQUIRED )



include_directories( 
    ${OpenCV_INCLUDE_DIRS} 
    inc
)
add_definitions( 
    # -DMY_DEBUG      # Print debug info and dump intermediate images 
    # -DPROFILING     # Profiling performance function-wise
    # -DGEAR360_C200  # Setting for GEAR 360 C200 camera 
)

# Add source to this project's executable.
add_executable (StitcherApp src/StitcherApp.cpp src/FishEyeStitcher.cpp inc/FishEyeStitcher.hpp inc/input_parser.hpp)

target_link_libraries( StitcherApp 
    #stitcher
    ${OpenCV_LIBS} 
)

set_target_properties( StitcherApp
    PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}\\output"
)
