set(EXE_NAME Lua)
set(ROOT_DIR "${CMAKE_CURRENT_SOURCE_DIR}")

exec_program(py ARGS "\"${CMAKE_SOURCE_DIR}/Tools/GenerateSources.py\" \"${ROOT_DIR}/src\" \"${ROOT_DIR}/_Sources.cmake\"")
include("${ROOT_DIR}/_Sources.cmake")

add_library(${EXE_NAME} STATIC ${headers} ${sources})
target_compile_definitions(${EXE_NAME} PRIVATE "_CRT_SECURE_NO_WARNINGS")

if(MSVC)
  target_compile_options(${EXE_NAME} PRIVATE "/MP")
endif()

