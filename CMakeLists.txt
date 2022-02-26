set(ROOT_DIR "${CMAKE_CURRENT_SOURCE_DIR}")

set(CMAKE_UNITY_BUILD true)
set(CMAKE_UNITY_BUILD_BATCH_SIZE 16)

include("${ROOT_DIR}/_Sources.cmake")

add_library(Lua STATIC ${headers} ${sources})

target_include_directories(Lua PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")

if(MSVC)
  target_compile_options(Lua PRIVATE "/MP")
endif()

