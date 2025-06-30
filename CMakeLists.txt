# If Lua is installed in a non-standard location, please set the LUA_DIR
# environment variable to point to prefix for the install. Eg:
#       Unix: export LUA_DIR=/home/user/pkg
#       Windows: set LUA_DIR=c:\lua51

cmake_minimum_required(VERSION 4.0)
project(lua-cjson C)

set(CJSON_SRC
    lua_cjson.c
    strbuf.c
    fpconv.c
)

add_library(cjson STATIC ${CJSON_SRC})

target_include_directories(cjson PRIVATE ${LUAJIT_INCLUDE_DIR})

target_compile_definitions(cjson PRIVATE
    MULTIPLE_THREADS
    LUA_VERSION_NUM=${LUA_VERSION_NUM}
)
target_compile_options(cjson PRIVATE -fPIC -O2)
# vi:ai et sw=4 ts=4:
