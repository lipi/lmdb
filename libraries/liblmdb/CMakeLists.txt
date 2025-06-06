cmake_minimum_required(VERSION 3.10)
project(liblmdb C)

# Compiler flags
set(CMAKE_C_STANDARD 99)
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

set(WARN_FLAGS "-Wall -Wno-unused-parameter -Wbad-function-cast -Wuninitialized")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${WARN_FLAGS} -O2 -g -pthread")

# Sources
set(LMDB_SOURCES mdb.c midl.c)
set(LMDB_HEADERS lmdb.h midl.h)

# Static library
add_library(liblmdb_static STATIC ${LMDB_SOURCES})
set_target_properties(liblmdb_static PROPERTIES OUTPUT_NAME "lmdb")

