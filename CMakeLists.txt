cmake_minimum_required(VERSION 3.5)
project(GDB-CMAKE)

set(CMAKE_CXX_STANDARD 11)
set(PROJECT_VERSION 1.0.0)

include_directories(${CMAKE_SOURCE_DIR}/A)

find_package(PythonInterp 3.5.2 REQUIRED)

execute_process(
 WORKING_DIRECTORY "${CMAKE_SOURCE_DIR}/A"
 COMMAND ${PYTHON_EXECUTABLE} ${CMAKE_SOURCE_DIR}/A/script.py
 COMMENT "Creating header"
)

set(HEADER_FILES
	${CMAKE_SOURCE_DIR}/A/index.h
)

set(SOURCE_FILES
        ${CMAKE_SOURCE_DIR}/main.cpp
	)

add_executable(output ${SOURCE_FILES} ${HEADER_FILES})

