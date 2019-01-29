cmake_minimum_required(VERSION 3.10)

set(CMAKE_CXX_STANDARD 11)
set(CXX_STANDARD_REQUIRED)

project(WindingNumber)

include (${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

set(PUBLIC_HEADER_FILES
  SYS_Math.h
  SYS_Types.h
  UT_Array.h
  UT_ArrayImpl.h
  UT_BVH.h
  UT_BVHImpl.h
  UT_FixedVector.h
  UT_ParallelUtil.h
  UT_SmallArray.h
  UT_SolidAngle.h
)

add_library(${PROJECT_NAME} STATIC UT_SolidAngle.cpp UT_Array.cpp)
set_target_properties(${PROJECT_NAME} PROPERTIES PUBLIC_HEADER "${PUBLIC_HEADER_FILES}")
target_link_libraries(${PROJECT_NAME} ${CONAN_LIBS})

configure_file(WindingNumberConfig.cmake.in WindingNumberConfig.cmake @ONLY)
