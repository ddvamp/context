cmake_minimum_required(VERSION 4.1)

project(
  context
  VERSION       0.1.0
  DESCRIPTION   "Context switch for fiber and coroutine"
  HOMEPAGE_URL  "https://github.com/ddvamp/context.git"
  LANGUAGES     CXX ASM
)

set(context_sources ${CMAKE_CURRENT_SOURCE_DIR}/src/exceptions_context.cpp)

list(
  APPEND context_sources
  ${CMAKE_CURRENT_SOURCE_DIR}/src/arch/x86_64/machine_context.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/src/arch/x86_64/machine_context_sysv_elf.S
)

add_library(context STATIC)
target_sources(context PRIVATE ${context_sources})

target_include_directories(
  context PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include
  context PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/src
)

target_compile_features(context PUBLIC cxx_std_23)

add_subdirectory(third_party)
target_link_libraries(context PUBLIC util)
