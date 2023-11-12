cmake_minimum_required(VERSION 3.5)
project(liblo-test)

# find_package(PkgConfig)
# if(PKG_CONFIG_FOUND)
#     pkg_check_modules(LIBLO liblo>=0.28)
# endif()
find_package(liblo)
message(LIBLO_VERSION)

add_executable(liblo-test main.cpp)
target_include_directories(liblo-test PRIVATE ${LIBLO_INCLUDE_DIRS})
target_link_libraries(liblo-test      PRIVATE ${LIBLO_LDFLAGS})

