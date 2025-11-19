cmake_minimum_required(VERSION 3.22)

project(TemplateApp
    VERSION
        0.0.1
    LANGUAGES
        C
        CXX
)

add_executable(${PROJECT_NAME})

target_sources(${PROJECT_NAME}
    PRIVATE
        src/main.c
        src/hello.c
        include/hello.h
)

target_include_directories(${PROJECT_NAME}
    PRIVATE
        include
)