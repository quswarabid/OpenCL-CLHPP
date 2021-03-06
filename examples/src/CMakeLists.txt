set(TRIVIALCL2_SOURCES
    trivialCL2.cpp )

set(TRIVIALCL2_HEADERS
    ${CLCPP_SOURCE_DIR}/include/CL/cl2.hpp)

set(TRIVIALCL2_SIZET_COMPAT_SOURCES
    trivialCL2SizeTCompat.cpp )

set(TRIVIALCL2_SIZET_COMPAT_HEADERS
    ${CLCPP_SOURCE_DIR}/include/CL/cl2.hpp)

set(HEADEREXAMPLECL2_SOURCES
    headerexampleCL2.cpp )

set(HEADEREXAMPLECL2_HEADERS
    ${CLCPP_SOURCE_DIR}/include/CL/cl2.hpp)

include_directories(
    ${CLCPP_SOURCE_DIR}/include
    ${OPENCL_DIST_DIR}/include
    ${OPENCL_INCLUDE_DIR})

link_directories( ${OPENCL_LIB_DIR} )

if( MSVC )
  set(CMAKE_CXX_FLAGS " -W3 /EHsc" )
elseif( CMAKE_COMPILER_IS_GNUCXX )
  set(CMAKE_CXX_FLAGS "-Wall" )
elseif( CMAKE_CXX_COMPILER_ID STREQUAL "Clang" )
  set(CMAKE_CXX_FLAGS "-Wall" )
endif()

add_executable(trivialCL2 ${TRIVIALCL2_SOURCES} ${TRIVIALCL2_HEADERS})
target_link_libraries( trivialCL2 OpenCL )

add_executable(trivialCL2SizeTCompat ${TRIVIALCL2_SIZET_COMPAT_SOURCES} ${TRIVIALCL2_SIZET_COMPAT_HEADERS})
target_link_libraries( trivialCL2SizeTCompat OpenCL )

add_executable(headerexampleCL2 ${HEADEREXAMPLECL2_SOURCES} ${HEADEREXAMPLECL2_HEADERS})
target_link_libraries( headerexampleCL2 OpenCL )
