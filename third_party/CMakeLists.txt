cmake_minimum_required(VERSION 4.1)

include(FetchContent)

FetchContent_Declare(
  util
  GIT_REPOSITORY  https://github.com/ddvamp/util.git
  GIT_TAG         origin/main
  GIT_SHALLOW     ON # Только указанный тэг, без всей истории ветки
  GIT_PROGRESS    OFF # Полезно включать для больших зависимостей
  # SOURCE_DIR
  # BINARY_DIR
)

FetchContent_MakeAvailable(util) # Должен быть расположен после всех FetchContent_Declare
