# =============================================================================
# Initialization
# =============================================================================

cmake_minimum_required(VERSION 2.9)
project(main CXX)

# =============================================================================
# Project dependencies
# =============================================================================

# -----------------------------------------------------------------------------
# Gettext
# -----------------------------------------------------------------------------
#find_package(Gettext)
#find_package(wxWidgets REQUIRED)
#include(${wxWidgets_USE_FILE})

# =============================================================================
# Build process
# =============================================================================

# -----------------------------------------------------------------------------
# Source files
# -----------------------------------------------------------------------------

# Set compiler parameters
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -s -Wall -Wextra -Wpedantic")

# Sources
file(GLOB SRC_FILES *.cpp *.hpp)

# Compile the main executable
add_executable(${CMAKE_PROJECT_NAME} ${SRC_FILES})
#target_link_libraries(${CMAKE_PROJECT_NAME} ${wxWidgets_LIBRARIES})

# =============================================================================
# Install process
# =============================================================================

# Define the files location during install process
install(TARGETS ${CMAKE_PROJECT_NAME} DESTINATION "bin")

# =============================================================================
# Custom targets
# =============================================================================

# Define the 'run' target
add_custom_target(run
    COMMAND ${CMAKE_PROJECT_NAME}
    DEPENDS ${CMAKE_PROJECT_NAME}
    WORKING_DIRECTORY ${CMAKE_PROJECT_DIR}
)
