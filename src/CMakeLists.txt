set(CMAKE_BUILD_TYPE Release)
add_executable(nsrlsvr handler.cc main.cc to_pair64.cc)
set_property(TARGET nsrlsvr PROPERTY CXX_STANDARD 14)
set_property(TARGET nsrlsvr PROPERTY CXX_STANDARD_REQUIRED true)
add_definitions(-DPKGDATADIR="${PKGDATADIR}")
add_definitions(-DPACKAGE_VERSION="${PACKAGE_VERSION}")
add_definitions(-DPACKAGE_URL="http://rjhansen.github.io/nsrlsvr")
add_definitions(-DPACKAGE_BUGREPORT="rjh@sixdemonbag.org")
install(TARGETS nsrlsvr RUNTIME DESTINATION bin)

configure_file(nsrlupdate.in ${CMAKE_BINARY_DIR}${CMAKE_FILES_DIRECTORY}/nsrlupdate)
file(COPY ${CMAKE_BINARY_DIR}${CMAKE_FILES_DIRECTORY}/nsrlupdate
  DESTINATION ${CMAKE_BINARY_DIR}
  FILE_PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ
  GROUP_EXECUTE WORLD_READ WORLD_EXECUTE)
install(PROGRAMS ${CMAKE_BINARY_DIR}/nsrlupdate DESTINATION bin)
