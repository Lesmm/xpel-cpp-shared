project(VisionCameraPipeline)
cmake_minimum_required(VERSION 3.9.0)

set(PACKAGE_NAME "XpCppShared")
set(BUILD_DIR ${CMAKE_SOURCE_DIR}/build)
set(CMAKE_VERBOSE_MAKEFILE ON)
set(CMAKE_CXX_STANDARD 17)

# Third party libraries (Prefabs)
find_library(LOG_LIB log)

# Add cpp sources
add_library(
        ${PACKAGE_NAME}
        SHARED
        # Java JNI
        src/main/cpp/XpPlaceHolder.cpp
)

# Header Search Paths (includes)
target_include_directories(
        ${PACKAGE_NAME}
        PRIVATE
        "src/main/cpp"
)

# Link everything together
target_link_libraries(
        ${PACKAGE_NAME}
        ${LOG_LIB}                          # <-- Logcat logger
        android                             # <-- Android JNI core
)