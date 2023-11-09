cmake_minimum_required(VERSION 3.5)
project(liblo-test)

if(MSVC)
  SET(CMAKE_LIBRARY_PATH_FLAG "-LIBPATH:")
endif()

find_package(PkgConfig)
if(PKG_CONFIG_FOUND)
    if(MSVC)
	    x_vcpkg_pkgconfig_get_modules(PREFIX LIBLO MODULES LIBLO LIBRARIES CFLAGS)
    else()
	    pkg_check_modules(LIBLO liblo>=0.28)
    endif()
endif()


add_executable(liblo-test main.cpp)
target_include_directories(liblo-test PRIVATE ${LIBLO_INCLUDE_DIRS})
target_link_libraries(liblo-test      PRIVATE ${LIBLO_LDFLAGS})

