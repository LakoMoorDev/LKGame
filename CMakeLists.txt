cmake_minimum_required(VERSION 3.0.0)

project(LKGame VERSION 0.1.0)

option(BUILD_SHARED_LIBS "Build Shared Libraries" ON) 

set(CMAKE_CXX_STANDARD_LIBRARIES "-static-libstdc++ -static-libgcc -Wl,-Bstatic -lstdc++ -lpthread -Wl,-Bdynamic")



#LKBox
add_subdirectory(lib/LKBox)

include_directories(lib/LKBox/include/)
link_directories(lib/LKBox)


#Debug
if(CMAKE_BUILD_TYPE STREQUAL "Debug")
        set(EXECUTABLE_OUTPUT_PATH "../Building/Debug/bin")
endif()

#Release (Hide console)
if(CMAKE_BUILD_TYPE STREQUAL "Release")
        set(EXECUTABLE_OUTPUT_PATH "../Building/Realese/bin")
        set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "../Building/Realese/bin")
        set(CMAKE_CXX_FLAGS "-mwindows")
        
endif()

#set(CMAKE_CXX_FLAGS "-mwindows")

#for icon =   windres LKBox.rc -o icon.o 



add_executable(
        LKGame
        src/main.cpp 
)
target_link_libraries(LKGame PUBLIC LKBox)
