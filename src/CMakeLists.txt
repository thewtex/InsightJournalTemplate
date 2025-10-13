cmake_minimum_required(VERSION 3.16.3)

# Set project name and description
project(InsightJournalTemplate
  VERSION 1.0.0
  DESCRIPTION "Template for Insight Journal submissions with ITK image processing examples"
  LANGUAGES CXX
)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)

# Find ITK
find_package(ITK REQUIRED)
include(${ITK_USE_FILE})

# Enable testing
include(CTest)
enable_testing()

# Add executables
add_executable(ImageCompare ImageCompare.cxx)
target_link_libraries(ImageCompare PUBLIC ${ITK_LIBRARIES})

add_executable(ImageCopy ImageCopy.cxx)
target_link_libraries(ImageCopy PUBLIC ${ITK_LIBRARIES})

# Add tests
add_test(
  NAME CreateImage
  COMMAND ImageCopy ${CMAKE_CURRENT_SOURCE_DIR}/../data/img1.png
)

add_test(
  NAME CompareImage
  COMMAND ImageCompare ${CMAKE_CURRENT_SOURCE_DIR}/../data/img1.png ${CMAKE_CURRENT_SOURCE_DIR}/../data/img1.png.base.png
)
