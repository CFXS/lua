set(EXE_NAME Lua)
set(ROOT_DIR "${CMAKE_CURRENT_SOURCE_DIR}")

set(CMAKE_UNITY_BUILD true)
set(CMAKE_UNITY_BUILD_BATCH_SIZE 16)

include("${ROOT_DIR}/_Sources.cmake")

add_library(${EXE_NAME} STATIC ${headers} ${sources})

target_include_directories(${EXE_NAME} PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}")

if(MSVC)
  target_compile_options(${EXE_NAME} PRIVATE "/MP")
endif()

