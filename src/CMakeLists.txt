find_package(fmt CONFIG REQUIRED)
find_package(spdlog CONFIG REQUIRED)
find_package(docopt CONFIG REQUIRED)

# Generic test
add_executable(intro main.cpp)
target_link_libraries(
  intro
  PRIVATE project_options
          project_warnings
          fmt::fmt
          spdlog::spdlog)

if(NOT MSVC)
  target_link_libraries(
    intro
    PRIVATE docopt_s)
else()
  target_link_libraries(
    intro
    PRIVATE docopt)
endif()