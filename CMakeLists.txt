cmake_minimum_required(VERSION 3.14)

project(PasswordManager
    VERSION 0.1.0
    DESCRIPTION "A password manager"
    LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Dependency
find_package(SQLite3 REQUIRED)

# Main Executable
add_executable(password_manager
    src/main.cpp
)

target_include_directories(password_manager PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

target_link_libraries(password_manager PRIVATE
    SQLite::SQLite3
)

# Testing
enable_testing()
add_subdirectory(tests)
