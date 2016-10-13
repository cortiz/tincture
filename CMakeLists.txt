cmake_minimum_required (VERSION 3.6.2)
project (tincture)

# The version number.
set (TINCTURE_VERSION_MAJOR 0)
set (TINCTURE_VERSION_MINOR 1)
set (TINCTURE_VERSION_MICRO 0)

find_package(wxWidgets COMPONENTS core base REQUIRED)
include( "${wxWidgets_USE_FILE}" )
# configure a header file to pass some of the CMake settings
# to the source code
configure_file (
  "${PROJECT_SOURCE_DIR}/src/Config.h.in"
  "${PROJECT_BINARY_DIR}/Config.h"
  )

file(GLOB_RECURSE TINCTURE_SRC
  "src/*.h"
  "src/*.cpp"
)

include_directories("${PROJECT_BINARY_DIR}")
add_executable(
    ${PROJECT_NAME}
    ${TINCTURE_SRC}
    )
target_link_libraries(
    ${PROJECT_NAME}
    ${wxWidgets_LIBRARIES}
)
