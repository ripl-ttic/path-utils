cmake_minimum_required(VERSION 2.6.0)

# pull in the pods macros. See cmake/pods.cmake for documentation
set(POD_NAME path-utils)
include(cmake/pods.cmake)

# The BASE_PATH is where the models, data, config, etc. directories are located
if (NOT BASE_PATH)
    set(BASE_PATH ${CMAKE_INSTALL_PREFIX})
else (NOT EXISTS ${BASE_PATH})
    message(WARNING "${BASE_PATH} is not a valid directory. Setting BASE_PATH: ${CMAKE_INSTALL_PREFIX}")
    set(BASE_PATH ${CMAKE_INSTALL_PREFIX})
endif()

message(STATUS "BASE_PATH: ${BASE_PATH}")

#tell cmake to build these subdirectories
add_subdirectory(src)
add_subdirectory(python)

#install the remote daemon launcher
install(PROGRAMS launchRemoteDaemon.sh DESTINATION bin)
