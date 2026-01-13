
# минимальная версия CMake
cmake_minimum_required(VERSION 3.20)

# имя проекта, язык и версия
project(nodo VERSION 1.0.0 LANGUAGES C)

# стандарт C
set(CMAKE_C_STANDARD 17)
set(CMAKE_C_STANDARD_REQUIRED ON)

# ========== библиотека ==========
add_library(node SHARED
    src/node.c
)

# путь к заголовкам
target_include_directories(node PUBLIC
    ${PROJECT_SOURCE_DIR}/include
)

# версия библиотеки (для .so)
set_target_properties(node PROPERTIES
    VERSION ${PROJECT_VERSION}
    SOVERSION 1
)

# ========== тесты ==========
add_executable(tests_node
    tests/tests_node.c
)

target_link_libraries(tests_node PRIVATE
    node
)
