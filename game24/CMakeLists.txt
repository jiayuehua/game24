find_package(range-v3 CONFIG REQUIRED)
find_package(fmt CONFIG REQUIRED)
find_package( Threads  REQUIRED )

# Generic test that uses conan libs
function(aoc arg)
add_executable(${arg} exprs.cpp "${arg}.cpp"  )
find_path(BOOST_SPIRIT_INCLUDE_DIRS "boost/spirit.hpp")

target_include_directories(${arg} PRIVATE
          ${CMAKE_CURRENT_SOURCE_DIR} 
          ${BOOST_SPIRIT_INCLUDE_DIRS}
#${Boost_INCLUDE_DIRS}
           )
target_link_libraries(
  ${arg} PRIVATE project_options project_warnings fmt::fmt-header-only
                Threads::Threads   range-v3 range-v3-meta range-v3::meta range-v3-concepts ${Boost_LIBRARIES} )
                   endfunction()
                   aoc(stl_with_lambda)
                   aoc(game24)
