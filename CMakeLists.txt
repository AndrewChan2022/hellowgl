cmake_minimum_required(VERSION 3.1)

#add_definitions(-DEXCLUDE_LOG_MODULE)
#add_compile_definitions(MG_ENABLE_OPENSSL=1)

# cpp version (be different for other platform, TODO).
set(CMAKE_CXX_STANDARD 17)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

project(hellowgl)


################## src
# add .cpp
file(GLOB mysrc "./src/*.cpp" "./src/*.h" "./src/*.hpp")


# add include directory
include_directories(./src)


################## include
# add all source files
add_executable(hellowgl WIN32 
    ${mysrc}
)

################## link
# opengl32.lib glu32.lib
find_package(OpenGL REQUIRED)
find_package(GLU REQUIRED)

include_directories( ${OPENGL_INCLUDE_DIRS}  ${GLU_INCLUDE_DIRS} )
target_link_libraries(hellowgl ${OPENGL_LIBRARIES} ${GLU_LIBRARY} )