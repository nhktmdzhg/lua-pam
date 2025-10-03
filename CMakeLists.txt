cmake_minimum_required(VERSION 3.15)
project(lua_pam)

set(CMAKE_CXX_STANDARD 14)

# Find Lua 5.3 specifically
find_package(Lua 5.3 EXACT REQUIRED)

# Find PAM library
find_library(PAM_LIBRARY pam REQUIRED)

set(SOURCE_DIR src)

add_library(lua_pam SHARED ${SOURCE_DIR}/main.cpp)

# Include Lua headers
target_include_directories(lua_pam PRIVATE ${LUA_INCLUDE_DIR})

# Link against Lua 5.3 and PAM
target_link_libraries(lua_pam ${LUA_LIBRARIES} ${PAM_LIBRARY})
