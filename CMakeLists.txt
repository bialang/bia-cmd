cmake_minimum_required(VERSION 3.1)

project(bia-cmd
	VERSION 0.0.0
	LANGUAGES CXX)

find_package(bia REQUIRED)

configure_file("${CMAKE_CURRENT_SOURCE_DIR}/config.hpp.in" "${CMAKE_CURRENT_SOURCE_DIR}/src/config.hpp")

file(GLOB_RECURSE sources
	"${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp")
add_executable(bia-cmd "${sources}")
target_link_libraries(bia-cmd PRIVATE bia::bia)
target_include_directories(bia-cmd
	PRIVATE "${CMAKE_SOURCE_DIR}/3rd_party/CLI11/include/")
set_target_properties(bia-cmd
	PROPERTIES OUTPUT_NAME "bia")

install(TARGETS bia-cmd
	RUNTIME DESTINATION "bin")
