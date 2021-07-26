cmake_minimum_required(VERSION 3.1)
project(nlohmann_json LANGUAGES CXX)

include(GNUInstallDirs)

add_library(nlohmann_json INTERFACE)
add_library(nlohmann_json::nlohmann_json ALIAS nlohmann_json)
target_include_directories(nlohmann_json
  INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

if (${CMAKE_VERSION} VERSION_LESS "3.8.0")
  target_compile_features(nlohmann_json INTERFACE cxx_range_for)
else()
  target_compile_features(nlohmann_json INTERFACE cxx_std_11)
endif()
