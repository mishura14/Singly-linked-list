
# минимальная версия CMake
cmake_minimum_required(VERSION 3.20)

# имя проекта, язык и версия
project(ListNode VERSION 1.0.0 LANGUAGES C)

# стандарт C
set(CMAKE_C_STANDARD 17)
set(CMAKE_C_STANDARD_REQUIRED ON)

# ========== библиотека ==========
add_library(ListNode SHARED
    src/list_node.c
)

# путь к заголовкам
target_include_directories(ListNode PUBLIC
    ${PROJECT_SOURCE_DIR}/include
)

# версия библиотеки (для .so)
set_target_properties(ListNode PROPERTIES
    VERSION ${PROJECT_VERSION}
    SOVERSION 1
)

# ========== тесты ==========
add_executable(tests_list_node
    tests/tests_list_node.c
)

target_link_libraries(tests_list_node PRIVATE
    ListNode
)
